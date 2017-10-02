
# INSTALLATION

You can use gcc-7 for compiling cathook if you add `-e CC=gcc-7 CXX=g++-7` to make command line

Ubuntu gcc6 installation: (check if you have gcc-6 installed already by typing `gcc-6 -v`
```bash
sudo apt update && sudo apt install build-essential software-properties-common -y && sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y && sudo apt update && sudo apt install gcc-snapshot g++-6-multilib gcc-6 g++-6 -y
```

Ubuntu other dependencies installation:

```bash
sudo apt update && sudo apt install git libssl-dev:i386 libc6-dev:i386 gdb libsdl2-dev libglew-dev:i386 libfreetype6-dev:i386 -y 
```


Arch gcc6 & dependencies installation:
```bash
sudo pacman -U https://archive.archlinux.org/packages/g/gcc-multilib/gcc-multilib-6.3.1-2-x86_64.pkg.tar.xz https://archive.archlinux.org/packages/g/gcc-libs-multilib/gcc-libs-multilib-6.3.1-2-x86_64.pkg.tar.xz https://archive.archlinux.org/packages/l/lib32-gcc-libs/lib32-gcc-libs-6.3.1-2-x86_64.pkg.tar.xz && sudo cp -r /usr/include/c++/6.3.1/ /tmp/ && sudo pacman -S gdb gdb-common glew1.10 glew lib32-glew1.10 rsync lib62-gcc-libs gcc-libs-multilib gcc-multilib --noconfirm && yes | sudo cp -r  /tmp/6.3.1/ /usr/include/c++/
```

If you don't use Ubuntu or Arch (or if Arch script gets outdated), here's the list of what cathook requires:

* `gcc-6`
* `g++-6`
* `gcc-6-multilib`
* `g++-6-multilib`
* `glew`
* `gdb` (for the injection script, you can use different injector if you want)
* `libssl-dev:i386`
* `libc6-dev:i386`
* `libsdl2-dev`
* `libglew-dev:i386`
* `libfreetype6-dev:i386`
* `rsync` (used for copying shaders/fonts to tf2 data directory, `check-data` script)


Cathook installation script:
```bash
git clone --recursive https://github.com/plasmafart/cathook && cd cathook && bash build-tf2
```

**Errors while installing?**

`/usr/include/c++/5/string:38:28: fatal error: bits/c++config.h: No such file or directory`
You don't have gcc-multilib-6 installed correctly.

`src/<any file>: fatal error: mathlib/vector.h: No such file or directory`
You didn't download Source SDK. **DO NOT DOWNLOAD CATHOOK USING "DOWNLOAD .ZIP" FROM GITHUB. USE git clone --recursive!**

If you are using another distro, make sure to have g++-6, gdb, libc6 and build essentials installed.

## Updating cathook
Run the `update` script in cathook folder.

Cathook requires a special data folder (contains shaders, font files, walkbot paths, etc). This folder is located at `/opt/cathook/data` and is generated automatically when you compile cathook.

## Injection
`sudo ./attach` to attach cathook into TF2. Optionally, you can provide an argument number (0-n - #) to provide the TF2 process ID (for bots).

`sudo ./attach-backtrace` to attach and print backtrace incase TF2 crashes. Some users report that this causes FPS drop in-game. This is recommended to grab a log of what went wrong if Cathook is crashing on you.

