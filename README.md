# WindowsDock

<p align="center">
  <b>macOS-inspired liquid-glass dock for Windows</b><br>
  A translucent, rounded-corners, GPU-friendly dock with auto-hide and dynamic application icons.
</p>

<p align="center">
  <a href="https://github.com/ramtnv/WindowsDock/issues"><img src="https://img.shields.io/github/issues/ramtnv/WindowsDock" alt="Issues"></a>
  <a href="https://github.com/ramtnv/WindowsDock/forks"><img src="https://img.shields.io/github/forks/ramtnv/WindowsDock" alt="Forks"></a>
  <a href="https://github.com/ramtnv/WindowsDock/stargazers"><img src="https://img.shields.io/github/stars/ramtnv/WindowsDock" alt="Stars"></a>
  <a href="https://github.com/ramtnv/WindowsDock/blob/main/LICENSE"><img src="https://img.shields.io/github/license/ramtnv/WindowsDock" alt="License"></a>
</p>

---

## ✨ Features

- **Liquid-glass aesthetic** – translucent acrylic-style backdrop with rounded corners, accent-colored edge border, and smooth hover states
- **Vertical dock** positioned on any screen edge (right, left, top, bottom)
- **Auto-hide** – slides out when the mouse leaves the edge-proximity zone; slides back in on approach (hysteresis keeps it visible while you interact)
- **50% dock height** – dock occupies half the screen height, starting at the top of the work area
- **Dynamic shortcuts** – automatically fetches and displays each application's original icon via Win32 `SHGetFileInfo`
- **Settings panel** – open via the `⚙` gear icon at the bottom of the dock; customize transparency, UI scale, dock height, tint color, accent color, position, auto-hide threshold, and monitor
- **Shortcut management** – add `.exe`/`.lnk` shortcuts, remove them, and click any shortcut to launch the app
- **Zero-dependency** – pure Python 3 + `tkinter` + `ctypes` (Win32 API); no installers or build tools required

---

## 📦 Quick Start

### Prerequisites

- Windows 10 or 11
- Python 3.11+ (installed from python.org or Microsoft Store)

### Run

```bash
# Clone the repo
git clone https://github.com/ramtnv/WindowsDock.git
cd WindowsDock

# Launch the dock
python main.py
```

Quit the dock by pressing **`Esc`**.

### Build a standalone `.exe` (optional)

```bash
pip install pyinstaller
pyinstaller --onefile --windowed --name LiquidGlassDock main.py
```

---

## 🎛️ Usage

| Action | How |
|--------|-----|
| Open settings | Click the **`⚙`** gear icon at the bottom of the dock |
| Launch app | Click any shortcut icon |
| Remove shortcut | Right-click a shortcut → **Remove** |
| Add shortcut | Settings → **Add shortcut** → select an `.exe` or `.lnk` |
| Quit dock | Press **`Esc`** |

Settings persist automatically to `%APPDATA%\LiquidGlassDock\config.json`.

---

## 🗂️ Project Structure

```
WindowsDock/
├── main.py          # Dock shell, auto-hide, shortcuts, icon extraction, settings
└── README.md        # This file
```

`main.py` is a single self-contained file (~860 lines) using only the Python standard library:
- `tkinter` – dock window, canvas rendering, settings UI
- `ctypes` – Win32 API (`user32`, `shell32`, `gdi32`) for cursor position, `SHGetFileInfo` icon extraction, DPI awareness, and window attributes
- `json` – config persistence

---

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Esc` | Quit the dock |

---

## 🖼️ Screenshots

<p align="center">
  <img src="docs/screenshot-dock.png" alt="Dock on right edge" width="300"><br>
  <em>Liquid-glass dock on the right screen edge</em>
</p>

<p align="center">
  <img src="docs/screenshot-settings.png" alt="Settings window" width="500"><br>
  <em>Settings panel — appearance, positioning, shortcuts</em>
</p>

> Add your own screenshots to `docs/` and update the paths above.

---

## 🛠️ Configuration

Configuration is stored in `%APPDATA%\LiquidGlassDock\config.json`:

```json
{
  "position": "right",
  "autoHide": true,
  "proximityThreshold": 25,
  "monitor": "primary",
  "transparency": 0.85,
  "scale": 100,
  "dockHeightPct": 50,
  "tintColor": "#1a1a24",
  "accentColor": "#00d2ff",
  "shortcuts": [
    {
      "id": "...",
      "name": "notepad.exe",
      "targetPath": "C:\\Windows\\System32\\notepad.exe"
    }
  ]
}
```

Edit by hand or through the settings UI; changes apply live.

---

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m "Add your feature"`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines (to be added).

---

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

---

## 🙏 Acknowledgments

- Inspired by macOS Dock and the liquid-glass design language
- Built with Python `tkinter` and the Windows Win32 API

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/ramtnv">ramtnv</a>
</p>
