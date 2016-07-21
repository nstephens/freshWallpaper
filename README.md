# freshWallpaper
## what, *another* shellscript to pull wallpaper from reddit?
## (yes, but it's mine)

Supported Desktop Environment: Ubuntu with Xfce4

Bash script with a smidge of python for json parsing

## What does it do
Automatically pulls new/random wallpaper from a list (you supply, or it does) of subreddits.  Then sets your desktop background to use it, and supports making something a favorite or blacklisting the image

## Logical process flow

- grabs a random subreddit from the list in $subredditDir
- checks if we have a recent (3hrs) json from that subreddit, grabs fresh if not
- chooses a random image from the json
- checks to see that the image is not in our history (already have it) or blacklist (hate it)
- downloads the image and ensures it made it to disk
- checks the aspect ratio and ensures that it is suitable for a desktop
- if all of that passes, then it will set the wallpaper on your desktop
- otherwise, it will loop a number of times before giving up

## Additional options
[ favorite | blacklist ]

freshWallpaper blacklist
deletes the current wallpaper, adds it to the blacklist so it won't download again, and grabs a fresh one

freshWallpaper favorite
adds the current wallpaper to your Favorites directory

## Supports cron automation
Can automatically determine your Xfce session, so that the script can be run from cron in an automated fashion

eg: */30 * * * *	/home/nick/bin/freshWallpaper >> /home/nick/.wallpapers/wallpaper.log 2>&1

