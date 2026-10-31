# PMR Tuner

A small offline web app that maps PMR446 channels and CTCSS codes to their
frequencies and tones.

- **PMR**: channels 1–16, from 446.00625 MHz in 12.5 kHz steps.
- **CTCSS**: codes 1–51 plus Off, in the order printed on the radio's table
  (`frequencies.jpeg`). Codes 39 and 40 (69.3 Hz and 62.5 Hz) are out of
  order on purpose, to match that table.

Tap either readout at the top to switch between the channel and tone grids.
The last selection is kept in `localStorage`.

## Running

It's a single static page with no build step. Serve the directory over HTTP:

```sh
python3 -m http.server
```

Then open http://localhost:8000. Opening `index.html` directly also works, but
the service worker only registers over HTTP(S).

## Installing

The app ships a web manifest and a service worker (`sw.js`), so it can be added
to a phone's home screen and works offline once loaded. The service worker
caches the app shell when it installs and caches Google Fonts the first time
they're fetched. Bump `CACHE` in `sw.js` when you change any cached file.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: markup, styles and script |
| `sw.js` | Offline cache |
| `manifest.json` | PWA manifest |
| `icon.svg`, `icon-*.png`, `apple-touch-icon.png` | Icons |
| `frequencies.jpeg` | Reference table the CTCSS ordering comes from |
