# KP1 Sales Report — PWA Package

This package converts the KP1 Sales Report web app into an installable PWA
(Progressive Web App) for iOS and Android.

## Files in this package

| File                        | Purpose                                      |
|-----------------------------|----------------------------------------------|
| `index.html`                | Main app (now with PWA hooks)                |
| `sw.js`                     | Service worker (offline + auto-update)       |
| `manifest.json`             | PWA manifest (name, icons, theme)            |
| `icon-192.png`              | App icon, 192×192 (Android)                  |
| `icon-512.png`              | App icon, 512×512 (Android splash, stores)   |
| `icon-512-maskable.png`     | Maskable icon for Android adaptive shapes    |
| `apple-touch-icon.png`      | App icon, 180×180 (iOS Home Screen)          |
| `favicon.png`               | Browser tab icon                             |

## ⚠ You also need `firebase-config.js`

Your existing `index.html` references `firebase-config.js`. That file is
NOT included in this package because it contains your Firebase credentials.
Upload your existing `firebase-config.js` to the same folder.

## Deploy steps (GitHub Pages)

1. Upload **all the files above** + your `firebase-config.js` to your GitHub
   repository root (overwrite the existing `index.html`).
2. Go to GitHub repo → Settings → Pages.
3. Set "Source" → Deploy from a branch → `main` → `/ (root)` → Save.
4. Wait ~1 minute for Pages to deploy.
5. Visit the live URL (e.g. `https://YOUR-USER.github.io/REPO/`).

## How to install on phone

### iPhone / iPad
1. Open the live URL in **Safari** (must be Safari, not Chrome).
2. Tap the **Share** icon → **Add to Home Screen** → **Add**.
3. App icon appears on Home Screen. Tap to launch fullscreen.

### Android
1. Open the live URL in **Chrome**.
2. Chrome will prompt with "Install app" automatically — tap **Install**.
3. Or tap **⋮ menu → Install app / Add to Home Screen**.
4. App icon appears in the app drawer and Home Screen.

## Updating the app later

Whenever you update `index.html`, also bump the cache version in `sw.js`:
```js
const CACHE_VERSION = 'kp1-report-v2'; // increment v1 → v2 → v3...
```
This forces all installed PWAs to discard old cache and reload the fresh app.

## Offline behaviour

- App shell (HTML/icons/manifest) is cached → app opens offline.
- Firebase reads/writes require network → those operations fail offline
  but the UI still loads, so the user sees what they can.

## Theme & icon

The icon uses the full Kailash Parbat banner logo on a white background,
sized so it remains readable down to ~48px in Android's app switcher.
Theme colour `#060e18` (dark navy) is applied to the status bar.
