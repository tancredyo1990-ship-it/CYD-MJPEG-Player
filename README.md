# CYD-MJPEG-Player

An expanded and enhanced version of The Last Outpost Workshop's ESP32-2432S028 video player, adding a touch-controlled interface, video library, playback modes and more.

**Author:** DMPumuki ([GitHub profile](https://github.com/tancredyo1990-ship-it))

## Overview

CYD MJPEG Player is an enhanced version of the original MJPEG video player developed by **[The Last Outpost Workshop](https://github.com/thelastoutpostworkshop)** for the ESP32-2432S028 Cheap Yellow Display (CYD).

The original project provides MJPEG video playback using videos converted with an online tool. This version expands the original player with touch controls, an interactive video library, configurable playback modes and additional settings.

## Requirements and Important Notes

- **Compatible hardware:** ESP32-2432S028 CYD with an ILI9341 display controller.
- **Touchscreen input:** A stylus pen is recommended for easier and more precise interaction with the interface.
- **Video format:** Videos must be converted to the supported MJPEG format before being copied to the microSD card.
- **No audio:** Video playback is silent. Audio is not supported.
- **microSD format:** The microSD card must be formatted using the FAT32 file system.
- **Video location:** MJPEG files must be placed inside a folder named `mjpeg` in the root directory of the card.

## Features

### Video Playback

- **Touch brightness control:** Slide your finger vertically across the screen to adjust the display brightness during playback.
- **Next video:** Tap the right side of the screen to display a "Next video" notification and skip to the next video.
- **Previous video:** Tap the left side of the screen to display a "Previous video" notification and return to the previous video.
- **Return to main menu:** A downward arrow HUD button allows you to return to the main menu during playback.
- **Configurable HUD:** Enable or disable the return arrow from the settings menu.

### Playback Modes

The main menu provides three playback options:

- **Sequential:** Play videos in order. The playback logic is designed to return to the first video after reaching the end of the list.
- **Random:** Play videos in a shuffled order. The list is shuffled again after each complete cycle.
- **Repeat:** Continuously repeat the same video.

### Video Library

The video library provides a visual overview of the videos stored on the microSD card.

- Displays thumbnail previews of six videos per page.
- Shows each video's filename and file size.
- Touch a video preview to play it.
- Access individual video information.

### Settings

The settings menu provides:

- Display brightness adjustment.
- Enable or disable the return arrow HUD displayed during video playback.

## Flashing the Firmware (Beginner's Guide)

Want to try the player? Getting it onto your CYD is quite simple. You don't need any special programming equipment or software.

### What do you need?

- An ESP32-2432S028 Cheap Yellow Display (CYD).
- A USB cable to connect it to your computer.

That's it!

### Step 1: Download the firmware

Go to the [Releases](https://github.com/tancredyo1990-ship-it/CYD-MJPEG-Player/releases) section of this repository.

Download the `.bin` firmware file attached to the latest release.

### Step 2: Open the web flasher

Visit [ESP Web Tool](https://esptool.spacehuhn.com/) using a compatible browser, such as Google Chrome or Microsoft Edge.

This website allows you to flash ESP32 firmware directly from your browser.

### Step 3: Connect your CYD

Connect your CYD to your computer using the USB cable.

On the ESP Web Tool website:

1. Select the option to connect to your device.
2. Choose the serial port corresponding to your CYD.
3. Allow the browser to access the serial port when prompted.

### Step 4: Flash the firmware

1. Select the option to choose a firmware file.
2. Load the `.bin` file you downloaded earlier.
3. Set the flash address to `0x0` if the tool asks for one.
4. Start the flashing process and wait for it to finish.

Once the process is complete, your CYD should be ready to run the player!

## Preparing the microSD Card

Before using the player, format your microSD card with the **FAT32** file system.

Create a folder named `mjpeg` in the root directory of the card. Copy all your converted `.mjpeg` video files directly into this folder.

The folder structure should look like this:

```text
microSD/
└── mjpeg/
    ├── video1.mjpeg
    ├── video2.mjpeg
    ├── video3.mjpeg
    └── video4.mjpeg
```

**Important:**
- The folder name must be exactly `mjpeg`.
- Video files must be placed directly inside this folder, not in additional subfolders.
- Only non-empty files with the `.mjpeg` extension are recognized.
- The current firmware is configured to register up to **2,000 video files**.

## Video Conversion

Videos must be converted to the MJPEG format supported by the player before copying them to the microSD card.

The original project uses **Video Conversion Studio**, an online conversion tool developed by The Last Outpost Workshop.

[Open Video Conversion Studio](https://thelastoutpostworkshop.github.io/video_conversion/)

Remember that videos are played without sound.

## Testing and Known Limitations

The current version has been tested with a small video collection. Some aspects still require further testing.

### Pending Tests

- **Large video libraries:** Test playback and navigation with a significantly larger number of videos, approaching the configured limit of 2,000 files. So far, testing has been performed with seven videos, including one file approximately 2 GB in size.
- **Complete sequential playback:** Verify a complete playback cycle, from the first video to the last, and confirm that playback automatically starts again from the beginning. The code is designed to do this, but a full cycle has not yet been confirmed because one of the test videos is approximately 90 minutes long.

These tests will help establish the reliability of the player when handling larger collections and extended playback sessions.

## Suggestions and Feedback

Suggestions, feedback and ideas for improving the player are always welcome!

If you have ideas for new features, interface improvements or ways to make the player more reliable, feel free to share them through the GitHub repository.

## Credits

This project is based on the original work by **[The Last Outpost Workshop](https://github.com/thelastoutpostworkshop)**.

- **Original project:** [ESP32-2432S028 Video Player](https://github.com/thelastoutpostworkshop/esp32-2432S028_video_player)
- **Original creator:** [The Last Outpost Workshop](https://github.com/thelastoutpostworkshop)
- **Video conversion tool:** [Video Conversion Studio](https://thelastoutpostworkshop.github.io/video_conversion/)
- **Modifications and extensions:** DMPumuki ([GitHub profile](https://github.com/tancredyo1990-ship-it))

## Development Acknowledgements

ChatGPT (OpenAI) was used as an AI-assisted development tool during the modification and expansion of the original codebase.

It provided assistance with code development, debugging, implementation of new features and technical problem-solving.

Hardware testing, feature decisions and project direction were carried out by DMPumuki.

## License

This project is derived from software originally released under the MIT License.

Please refer to the original repository and its license for the original project's copyright and licensing terms.
