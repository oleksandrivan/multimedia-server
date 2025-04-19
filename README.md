# 🎬 Self-Hosted Media Automation Stack

This repository contains a `docker-compose.yml` file for a complete self-hosted media automation setup using popular tools like **Sonarr**, **Radarr**, **Bazarr**, **Transmission**, **Prowlarr**, and **Overseerr**, all served securely via **Cloudflared**.

---

## 🧱 Services Overview

### 📺 Sonarr
- **Image:** `lscr.io/linuxserver/sonarr`
- TV show management and automation.
- Port: `52000` (web UI)
- Volumes:
  - Config: `/home/elucri/config/sonarr`
  - TV Library: `/home/elucri/Downloads/Torrents/Tv shows`
  - Downloads: `/home/elucri/Downloads/Torrents/Transmission`

### 🎞️ Radarr
- **Image:** `lscr.io/linuxserver/radarr`
- Movie management and automation.
- Port: `52003`
- Volumes:
  - Config: `/home/elucri/config/radarr`
  - Movies: `/home/elucri/Downloads/Torrents/Movies`
  - Downloads: `/home/elucri/Downloads/Torrents/Transmission`

### 🧩 Prowlarr
- **Image:** `lscr.io/linuxserver/prowlarr`
- Indexer manager and search proxy for Sonarr/Radarr.
- Port: `52001`
- Volume:
  - Config: `/home/elucri/config/prowlarr`

### 📝 Bazarr
- **Image:** `lscr.io/linuxserver/bazarr`
- Subtitles manager for Radarr and Sonarr.
- Port: `52002`
- Volumes:
  - Config: `/home/elucri/config/bazarr`
  - Movies: `/home/elucri/Downloads/Torrents/Movies`
  - TV Shows: `/home/elucri/Downloads/Torrents/Tv shows`

### ⬇️ Transmission
- **Image:** `lscr.io/linuxserver/transmission`
- BitTorrent client.
- Ports:
  - `52004`: Web UI
  - `51413`: TCP/UDP peer port
- Volumes:
  - Config: `/home/elucri/config/transmission`
  - Downloads: `/home/elucri/Downloads/Torrents/Transmission`
  - Watch folder: `/home/elucri/Downloads/Torrents/Watch`

### 📬 Overseerr
- **Image:** `lscr.io/linuxserver/overseerr`
- Web request management for movies and shows.
- Port: `52005`
- Volume:
  - Config: `/home/elucri/config/overseerr`

### 🌐 Cloudflared
- **Image:** `cloudflare/cloudflared:latest`
- Securely tunnels access to your services via Cloudflare.
- Requires a `.env` file with:
  ```env
  CLOUDFLARED_TOKEN=your_cloudflare_token_here

