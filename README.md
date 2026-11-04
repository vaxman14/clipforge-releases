# ClipForge downloads

Official customer downloads for ClipForge desktop releases.

## Ubuntu 24.04 / WSL2 (x86_64)

The current public prerelease is **ClipForge 0.1.3** for Ubuntu 24.04 LTS on WSL2 (`amd64`).
It is self-contained and installs the local application, CPU inference runtime, FFmpeg/ffprobe,
yt-dlp, Deno, and the production public licensing configuration. No signing key, API token,
customer record, or payment credential is included.

1. Download `clipforge_0.1.3_amd64.deb` and `SHA256SUMS` from the
   [v0.1.3 release](https://github.com/vaxman14/clipforge-releases/releases/tag/v0.1.3).
2. Verify the download:

   ```sh
   sha256sum -c SHA256SUMS
   ```

3. Install and launch:

   ```sh
   sudo apt install ./clipforge_0.1.3_amd64.deb
   clipforge
   ```

On first launch, ClipForge shows the licensing gate. Choose **Start Trial** to begin the
7-day trial, **Buy License** for Stripe-hosted purchase, or import/activate an existing
license. Installing the package alone does not start the trial.

For explicit CPU mode, run `clipforge --cpu`. NVIDIA WSL2 users can require CUDA Whisper
and NVENC readiness with `clipforge --gpu --readiness`; GPU mode fails closed rather than
silently using CPU. The release notes describe the current container qualification and the
remaining real Windows/WSL2 hardware checks.

### Uninstall

```sh
sudo apt remove clipforge
```

User projects and licenses remain under `~/.local/share/clipforge`. Use
`sudo apt purge clipforge` only when you also intend to remove package-owned configuration.

## ClipForge Recorder for macOS (Apple silicon and Intel)

ClipForge Recorder records scripted app demos on a Mac. Download `ClipForge-Recorder-<version>.dmg`
from the newest `recorder-v…` release, open it, and drag **ClipForge Recorder** onto **Applications**.
Requires macOS 15 or later.

After that it updates itself: **ClipForge Recorder > Check for Updates…**, or automatically once a day.
Updates replace the app in place, so there's nothing to uninstall, and your settings and the Screen
Recording and Accessibility permissions carry over.

Every build is signed with Developer ID Application: CTF Designs, LLC (9M4ZXKN97F), and each update is
also signed with the app's own update key, which the app checks before installing.
[`recorder/appcast.xml`](recorder/appcast.xml) is the update feed the app reads.
