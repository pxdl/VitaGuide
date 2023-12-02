# Welcome to the VitaGuide docs!

This page will guide you on how you to make an undubbed version of your own **Persona 4 GOLDEN** game. This guide covers both the **physical** and **digital** versions of the game.

**The links to the tools used for unpacking and repacking are down and are going to be updated soon. In the meantime, you can use the xdelta patch method.**

The cutscene undub is **complete**.

_The steps in this guide were written so that you can also learn how to mod other games._

## Installing Henkaku

* Make sure your Vita is on firmware version 3.60.
* Go to henkaku.xyz on your Vita.
* A popup will appear, touch the "Ok" button and wait for the browser to close.

_If the browser crashes, try deleting cookies, rebooting and rebuilding the database._

If you've done everything correctly, there should now be a molecularShell bubble on your Vita menu. You can use it to access your files, install .vpk homebrew and host a FTP server on your Vita.

## Installing VitaShell

* [Download the latest VitaShell (.vpk file)](https://github.com/TheOfficialFloW/VitaShell/releases/latest)

* Open your PS Vita settings, go to "Henkaku Settings", and check "Enable Unsafe Homebrew"

* Open molecularShell and press Select to start the FTP server. Make sure your Wi-Fi is turned on.

* Open your favorite FTP client on your computer and connect to your Vita.

Recommended settings for Filezilla:

![File -> Site Manager](https://i.imgur.com/lOwhLtM.png)
![Edit -> Settings -> Filetypes](https://i.imgur.com/066Ow9N.png)

* Copy `VitaShell.vpk` to `ux0:`

* Press `Circle` to close the FTP connection.

* Go to `ux0:`, press `X` on `VitaShell.vpk` and press `X` again to install it.

You can now use VitaShell instead of molecularShell.

## Dumping your game

> `PCSE00120` is the TITLEID for the **American** version of Persona 4 GOLDEN.

> `PCSB00245` is the TITLEID for the **European** version of Persona 4 GOLDEN.

For this, we need to get the game's files while they are decrypted by the Vita.
To do this, we use VitaShell's PFS Decryption features.

* Open VitaShell on your Vita.
* Go to `ux0:app/` and highlight the game's TITLEID folder using the directional keys. **(Use `gro0` instead of `ux0` if you're dumping a physical game.)**. Press `Triangle`, go to `More` and then `Open Decrypted`.

You can now use FTP to access `ux0:app/[TITLEID]`, where your decrypted game files will be present. Use any FTP client you like on your PC to dump the game files to a safe location. **(Again, make sure to use `gro0` instead of `ux0` if you're dumping a physical game.)**

_For any game, you can also access the following locations with the `Open Decrypted` functionality:_
* `ux0:patch/[TITLEID]` - (Game Update)
* `ux0:addcont:[TITLEID]/` - (DLC Content)
* `ux0:user/00/savedata/[TITLEID]` - (Save)

If you want to manually extract, modify and repack the game files, you can skip to the ["Manual Methos"](https://github.com/s1cp/VitaGuide/wiki/Home/_edit#manual-method) section.

## Patch Method

This method is way simpler and makes use of an Xdelta patch. You just need to get your `data.cpk`, the patch, then open xdeltaUI, go to "Apply patch", select the correct files and it's done. MD5 hash included in README.txt.

You now have the undubbed `data.cpk` with just a few clicks.

>Your own repacked `data.cpk` will _probably_ have a different md5 checksum than the patched one because the `.cpk` holds data about how it was built, and any variation on that would change the hash. If you use the .xdelta patch, check the md5 hashes on this section.

### American version
**Latest 2.0 Patch (753,6 MiB) (Compressed, battle voices fixed)**
Magnet link: magnet:?xt=urn:btih:0f5b5b174fe91f59552ccfdc645b5f74c72665cc&dn=Persona%204%20GOLDEN%20Undub%20Patch%202.0

_The final **American** patched data.cpk file should have the following md5 checksum:_ `59a8b4c32ddfdb238f546120b6c494c3`

### European version

You can convert the American patch to the European patch easily by using another patch.

[Download this .xdelta file.](https://u.pomf.is/svjqmn.xdelta)

Patch the American Version patch previously mentioned (.xdelta file) with this patch.

It will generate a new .xdelta file. This will be the patch for your European data.cpk file.

_The final **European** patched data.cpk file should have the following md5 checksum:_ `d889e16b842e69ec2b7cd5a19f3e3fc0`

After patching your `data.cpk` file, skip to the ["Copying Back"](https://github.com/s1cp/VitaGuide/wiki/Home/_edit#copying-back) section.

## Manual method

### Unpacking the files

[Download these tools first.](https://u.pomf.is/pewhqk.zip)

After you've got your decrypted game files, store them in a safe place. Try not to change the original files and make a copy of what you are modding to keep things organized and to avoid copying the game's files again. Keep the folder structure intact because we'll need that later to patch the game.

Make 2 folders for your .cpk extraction, one for the English version and another for the Japanese version. You can find a Japanese dump at the Amicitia forum.

Extract `cpk_unpack.zip`, open the Windows CMD on the extracted folder, and type:
`cpk_unpack "Location of your data.cpk"`

Example:
`cpk_unpack C:\Users\User\Documents\PCSE00120\data\data.cpk`

The program will extract the .cpk's contents in a folder inside its own directory.

Do the same for the Japanese version.

Store the extracted contents in a separate folder. In our case, we could use something like `extracted_us` and `extracted_jp`.

>If you're working with an European version of the game, use `extracted_eu` to clear up some confusion.

### Replacing the files

Now, create a new folder. This folder will be the one where we will replace the sound files from the American/European version with the ones from the Japanese version of the game. We will be calling it `extracted_undub`

* Copy all the contents from the `extracted_us` (or `extracted_eu`) folder to `extracted_undub`. That will be our "base" game.
* Copy the `sound` folder from `extracted_jp` to `extracted_undub` and merge/replace all the files.
* Copy the `model\pack` folder from `extracted_jp` to `extracted_undub\model` and merge/replace all the files. This will fix some battle voices still being in English.

### Repacking the files

#### Uncompressed method

This method repackages the files _uncompressed_, taking almost 3gb of space. I decided to keep it because it uses a GUI and is more user friendly.

For the _compressed_ method, go to the next section.


* Extract the CriPackedFileMaker.zip file included in the "tools" download provided before.

* Run CriPackedFileMaker.exe

* Change the base directory by clicking on the folder icon on the top, and sekect the `extracted_undub` folder.

* If all the files are there, you can click the "Build CPK file..." button.

* Leave everything just like the following picture:

![Correct settings](https://u.pomf.is/rchrpx.png)

* Click "Start to Build"

* After it has finished packing the files, open CriPackedFileMaker.exe again.

* Click on the top right button that says "Open a CPK file" and select your newly packed data.cpk.

* Verify if it shows info similar to the following ones:

![Info](https://u.pomf.is/fjixzx.png)

* If everything seems correct, we can now put the file back on the Vita.

#### Compressed method

This method repackages the files _compressed_, taking almost half the space the file from the uncompressed method takes.

* Extract the CriPackedFileMaker.zip file included in the "tools" download provided before.

* Copy `cpkmakec.exe` and `CpkMaker.DLL` to the `extracted_undub` folder.

* [Download this .csv file.](https://u.pomf.is/wbotyk.csv). Rename it to `data.csv` put it inside the `extracted_undub` folder.

* Hold CTRL+SHIFT and right click on an empty space inside the folder. Click "Open Command Window Here". Or just `cd` into the `extracted_undub` folder using CMD.

* Type the following into CMD. The program will now repack all your files into a `data.cpk` file inside the `extracted_undub` folder:

`cpkmakec data.csv data.cpk -align=2048 -mode=FILENAME -code=UTF-8`

* After it has finished packing the files, open `CriPackedFileMaker.exe`.

* Click on the top right button that says "Open a CPK file" and select your newly packed `data.cpk`.

* Verify if it shows info similar to the following ones:

![Info](https://u.pomf.is/jqadyd.png)

* If everything seems correct, we can now put the file back on the Vita.

## Copying back

To mod Vita games we can't just replace the files in `ux0:app/[TITLEID]`, we need to put the modified files in `ux0:/patch`.

Persona 4 GOLDEN uses a single .cpk file for all its contents besides the manual and videos, so we need to copy the entire data.cpk we just created to our Vita. This makes the game take up twice the original space, but we have a workaround. We can just use an empty file named `data.cpk` to replace the one located in `ux0:app/[TITLEID]`. It will only look for the one in the `patch` folder.

**Make sure** you have a `param.sfo` file inside the `sce_sys` folder at `ux0:patch/[TITLEID]/sce_sys` or else the game won't boot. You can use the one from molecularShell located at `ux0:app/MLCL00001`if you're modding the digital version.

If you're modding the **physical** version of the game, we can't use molecularShell's `param.sfo`, you have to get the `param.sfo` file from your **decrypted** game dump we did before.

Open the `param.sfo` file using [this program](https://sites.google.com/site/theleecherman/sfoeditor) and change the `APP_VER` parameter of your game file and put something higher, like 1.01.

After doing this, put the edited `param.sfo` file in `ux0:patch/[TITLEID]/sce_sys`.

`ux0:/patch/PCSE00120/sce_sys` for the **American** version of Persona 4 GOLDEN.

`ux0:/patch/PCSB00245/sce_sys` for the **European** version of Persona 4 GOLDEN.

>We put the **modified** files in `ux0:patch/[TITLEID]` regardless if we're using a physical or digital game.

And last but not least, put the new `data.cpk` created from the files of `extracted_undub` inside `ux0:/patch/[TITLEID]/data`

## Cutscenes

The Persona 4 GOLDEN cutscenes aren't stored inside the `data.cpk` file, so it's easier for us to modify them. You just have to put your properly encoded video files inside `ux0:patch\[TITLEID]\data\movie` and rename them accordingly.

If you also want the cutscenes to be in Japanese, you can download the subbed videos using the following link:

### Subbed Japanese Cutscenes

Magnet link: magnet:?xt=urn:btih:a8fed57850eec56940566454f63ca524180cdfb3&dn=Persona%204%20GOLDEN%20Cutscene%20Undub

I have also included some files used in the subbing process inside the `Misc` folder.

## Done

The game should now boot and you can now play Persona 4 GOLDEN with Japanese voices.

You can try experimenting with the .mp4 files from the dumped game. It's possible to sub them and convert them back. You just have to use the same encoding options and put the file in the same structure as the game folder inside `app`, but inside the `patch` folder.

## Help

If you have any questions, feel free to create a new issue on GitHub.

## Credits

Thanks to:

* The Henkaku devs (@Yifanlu and others) for creating Henkaku and giving birth to the Vita homebrew scene.

* theflow0 for creating VitaShell and many other useful tools.

* @RyanShrinefox (for the tools used for data.cpk extraction, tips on compression and battle voices).

* @regularpanties (for providing the Japanese rip).

* Mr. Gas and Major Tom for the old PFS decryption process.

