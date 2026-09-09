# iptv-stream-manager
A lightweight Bash &amp; Dialog TUI for managing loopable IPTV UDP multicast streams via FFmpeg.

# IPTV Stream Manager (`iptv-streamer`)

A lightweight, terminal-based user interface (TUI) written in Bash for generating, broadcasting, and managing continuous IPTV UDP multicast streams using `ffmpeg` and `dialog`.

---

## Features

* **Interactive TUI:** Simple menu-driven interface powered by `dialog`.
* **Seamless Looping:** Broadcasts continuous video streams (`-stream_loop -1`) in compliance with standard MPEG-TS transport stream requirements.
* **Stream Management:** Real-time monitoring and stopping of active FFmpeg multicast streams.
* **Logging & Audit Trail:** Automatic logging of individual stream output and a consolidated operation history log (`channels_history.log`).

---

## Prerequisites

Ensure your system has `ffmpeg` and `dialog` installed:

```bash
# Debian / Ubuntu
sudo apt update && sudo apt install -y ffmpeg dialog

# RHEL / CentOS / Rocky Linux
sudo dnf install -y ffmpeg dialog

```

---

## Installation

1. Copy the script to `/usr/local/bin/iptv-streamer`:
```bash
sudo cp iptv-streamer.sh /usr/local/bin/iptv-streamer
sudo chmod +x /usr/local/bin/iptv-streamer

```


2. Create the required media upload directory and set appropriate permissions:
```bash
sudo mkdir -p /home/iptvstreamer/streams/uploads
sudo mkdir -p /var/log/iptv_channels
sudo chown -R $USER:$USER /home/iptvstreamer/streams/uploads /var/log/iptv_channels

```



---

## Usage

Run the menu interface from any terminal location:

```bash
iptv-streamer

```

### Options

1. **Create stream:**
* Select a media file from `/home/iptvstreamer/streams/uploads/`.
* Configure parameters: `Channel Name`, `Multicast IP` (e.g., `239.255.1.1`), `Port` (e.g., `1234`), and `Bitrate` (in kbps).
* Launch background stream.


2. **Active streams:** View currently running UDP streams, display associated PIDs, and terminate chosen streams.
3. **Exit:** Clear screen and close interface.

---

## Directory Structure

* **Media Directory:** `/home/iptvstreamer/streams/uploads/`
* **Log Directory:** `/var/log/iptv_channels/`
* **Stream History:** `/var/log/iptv_channels/channels_history.log`
