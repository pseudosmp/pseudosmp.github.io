---
layout: about
navname: caxton_tutorial

tabTitle: 'Set custom fonts in Minecraft! (Caxton mod)'
ogTitle: 'Set custom fonts in Minecraft! (Caxton mod)'
ogDesc: 'A tutorial on how to create a font resource pack for the caxton mod for Minecraft Java Edition'
ogImg: https://cdn.modrinth.com/data/k8iIgzXE/76574a31d3214bb952cc01e8b5085b6e9a365f27.png
ogURL: caxton_tutorial
---

### Introduction

Caxton is a mod for the Fabric and (Neo)Forge modloaders, that allows you to change the font in which all text in Minecraft is displayed. The mod supports Windows and Linux with no additional setup. If you are on macOS, [you would have to compile the plugin on your mac, directly from the source.](https://gitlab.com/Kyarei/caxton#building-from-source). Running `gradle build` on a mac should give you a working jar.

The way you change fonts using Caxton is by loading Caxton font resource packs. There are two included fonts which appear in your resource pack selection screen right after you install the mod. You can enable them and see all the fonts changed to your selection.
![image](https://raw.githubusercontent.com/pseudoforceyt/smp/master/docs/media/caxton/caxton_1.webp)
![image](https://raw.githubusercontent.com/pseudoforceyt/smp/master/docs/media/caxton/caxton_2.webp)
![image](https://raw.githubusercontent.com/pseudoforceyt/smp/master/docs/media/caxton/caxton_3.webp)

Now the question arises, *why* do I have to change the font? Minecraft's font is good! It fits the aesthetic of the game! Well, the default font has no issues until you introduce certain non-latin characters. The minecraft style, isnt adapted to these characters and therefore they look ugly. Some indic scripts are completely unreadable.
![image](https://raw.githubusercontent.com/pseudoforceyt/smp/master/docs/media/caxton/caxton_4.webp)

The included fonts may not be to your liking or may not have the characters you regularly use. This is where you have to make your own Caxton resource pack

### Making a Resource Pack:

This is how a Caxton resource pack's structure looks like. You can copy the [in-built resource pack](https://gitlab.com/Kyarei/caxton/-/tree/master/fabric/src/main/resources/resourcepacks?ref_type=heads) and modify it to make it easy. Here, `pseudoforceyt` is called the **namespace**. You can set it to anything you like. It will be used later in setting the font.
![image](https://raw.githubusercontent.com/pseudoforceyt/smp/master/docs/media/caxton/caxton_5.webp)

#### 1) pack.mcmeta
![image](https://github.com/pseudoforceyt/smp/assets/70620481/178327f3-92fb-4e4e-9955-e7a3e5d652a9)

Here, you will have to set the pack format and give your pack description. The pack format for each version of minecraft can be found [here](https://minecraft.wiki/w/Pack_format)

#### 2) pack.png (optional)
This is an optional file which gives your resource pack an icon. It must be a square png image file (preferrably 128x128) placed alongside pack.mcmeta

***

Now we can create the `assets` folder. This folder will contain two folders: `minecraft/font/` and `<namespace>/textures/font/` (/ meaning nested folders) (replace namespace with the name you chose. This tutorial uses 'pseudoforceyt')
The `minecraft/font/default.json` file is where we tell Caxton to replace minecraft's default font with our font.

#### 3) ```assets/<namespace>/textures/font/```
The `assets/<namespace>/textures/font/` folder is where our font files and each font's configuration will lie. You can visit [dafont.com](https://www.dafont.com/) or [fonts.google.com](https://fonts.google.com/) (or any other font site) and download your preferred font.

But make sure it has these 4 variants: Regular, Bold, Italic, Bold Italic. It's not a requirement though, if your favourite font does not have any of this variant, you'd have to sacrifice on the formatting. For example, if bold italic is not available, we can substitute it with the bold variant and it would work just fine, but bold italic text and bold text will be indistinguishable.

After you get your font files, make sure to not have any capital letters, non-english characters or symbols other than . or _ in their file names. Then we can write the configuration for them.
The configuration files must be named as shown. The font name with its extension and then .json.
![image](https://github.com/pseudoforceyt/smp/assets/70620481/0c6a27e8-8a99-4f02-a4d1-3136bc78c41c)

Putting `{"tech": "msdf"}` in each of these fonts will display them correctly. But if anything is not to your liking - like the size of the font, or if the characters are cutting off, stuff like that. There are finer controls offered by Caxton. We will take a look at the additional options after we finish making our resource pack.
![image](https://github.com/pseudoforceyt/smp/assets/70620481/559cf880-41bb-4355-8f7d-13e20c361c9d)

#### 4) ```assets/minecraft/font/default.json```
This is the final piece of the puzzle. [The format can be copied as is from the in-built resource pack of Caxton for now.](https://gitlab.com/Kyarei/caxton/-/blob/master/fabric/src/main/resources/resourcepacks/inter/assets/minecraft/font/default.json?ref_type=heads) Remember 1.20 changed something in the default font provider so the format of this file will be different on 1.20 as compared to prior versions. Make sure you copy it from the resource pack of your minecraft version. 

Then, for each of the `"file":` option, set the value to `"<namespace>:<font_name>"`. Replace <namespace> with the name you chose, and <font_name> with your font's name. (Notice the style mentioned above `"file"` and set the value appropriately!)
Your file should look like this (1.20):
![image](https://github.com/pseudoforceyt/smp/assets/70620481/30f9a23d-376e-469b-a32c-afb317946cc2)

(We will look at what `shadow_offset` is later)
If your font is displayed incorrectly, we would have to configure a few more things.

The pack is now ready for a test run! For easier "debugging", we'll copy just the folder (we don't zip it) to the resourcepacks folder and have it open while our game is running, so we can make quick changes and reload resources to quickly see the change.
![image](https://github.com/pseudoforceyt/smp/assets/70620481/cc5bb9d2-2904-418a-986e-6e6f40660d52)

After applying the resource pack, you should see your font change. If you don't, you have done something wrong! Check the logs to get more info on where you went wrong, or retrace your steps
![image](https://github.com/pseudoforceyt/smp/assets/70620481/2340f954-a3fc-4d83-8d90-747b794e63b9)

### Configuration:

[PENDING]
