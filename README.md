# egghead-video-download
Download Egghead.io video with ease and in highest speed


## Prerequesits
- You need nix box (Mac OS X, Linux ...)
- You need to download an install [youtube-dl](https://rg3.github.io/youtube-dl/) to download the videos
- You need to download and install Aria2c download manager, to accelerate the download process.
- You need to download and install Lynx console web browser, to dump the links

The following example are for Mac OS X

### Install youtube-dl using homebrew
`$ brew install youtube-dl`

### Install Lynx using homebrew
`$ brew install lynx`

### Install aria2c using homebrew
`$ brew install aria2`

Now that we installed all the prerequesits, we are ready to download lessons from Egghead

- First grab the desired lesson link, let say [https://egghead.io/courses/intro-to-angular-2-router](https://egghead.io/courses/intro-to-angular-2-router)
- Second will dump all lesson links using Lynx command into a text file say links.txt

`$ lynx -dump https://egghead.io/courses/intro-to-angular-2-router | awk '/lessons\//{print $2}' > links.txt`

- Download the video files

`$ youtube-dl -c -i -o "%(autonumber)s-%(title)s.%(ext)s" -a links.txt --external-downloader aria2c --external-downloader-args "-j1 -x16 -s16 -k1M"`
