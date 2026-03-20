# CastReader Chrome Extension (Bundled Build)

Pre-built Chrome Extension for the [CastReader OpenClaw Skill](https://github.com/vinxu/castreader-skills).

This extension is loaded by Puppeteer during book sync operations (Kindle/WeRead) and provides:
- **WeRead**: Canvas layout data interception + anti-piracy encryption filtering
- **Kindle**: KindleModuleManager token interception + tesseract-wasm OCR

## Usage

This repo is consumed automatically by the CastReader skill's `sync-books.js` script. You don't need to clone it manually.

When the skill runs and the extension is not found locally, it downloads this repo automatically:

```bash
# Automatic download happens inside sync-books.js
# Or manually:
git clone https://github.com/vinxu/castreader-extension.git chrome-extension
```

## Structure

```
├── manifest.json           # MV3 manifest
├── background.js           # Service Worker (TTS proxy, messaging)
├── content-scripts/
│   ├── kindle-hook.js      # Kindle: KindleModuleManager interception
│   ├── kindle-intercept.js # Kindle: main world token capture
│   ├── weread-hook.js      # WeRead: MutationObserver for preRenderContainer
│   └── weread-intercept.js # WeRead: main world fetch interception
├── chunks/                 # Shared code chunks
├── tesseract-wasm/         # tesseract-wasm OCR engine + trained data
├── ocr-offscreen.html      # Offscreen document for OCR
├── popup.html              # Extension popup UI
└── _locales/               # i18n (30+ languages)
```

## Version

Current: **v1.0.3** (matches Chrome Web Store release)

## Building from Source

If you have the main CastReader project (`readout-desktop`):

```bash
cd ~/Documents/MyProject/readout-desktop
pnpm build
# Output: .output/chrome-mv3/
```

## License

MIT
