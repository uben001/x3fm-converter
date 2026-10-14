# X3FM Converter

Open Sigma DP Merrill raw files (X3F) in Adobe Camera Raw with **the colour and detail of SIGMA Photo Pro**, then edit them with Camera Raw's full raw controls.

**Requires:** a DP1, DP2 or DP3 Merrill · macOS 14+ on Apple silicon · **SIGMA Photo Pro 6** installed · Adobe Camera Raw / Photoshop

**Download:** see [Releases](../../releases) → `X3FM-Converter-1.7.1.zip`

---

## Why it exists

The Merrill's Foveon sensor records red, green and blue in three stacked layers at every pixel. SIGMA Photo Pro is still the best renderer for these files, but it is a slow editor with few tools. Camera Raw is a great editor, but its own handling of Merrill files does not look like SPP.

X3FM Converter combines the two. It does not imitate SPP's look: it has SPP's own processing engine render each file, then turns that result back into a raw DNG that Camera Raw can edit freely.

## How a file is converted

1. **Read** the X3F: raw sensor data, the camera's white-balance preset and any edits saved in SPP.
2. **Render** with SIGMA Photo Pro's installed engine: colour, noise reduction, sharpening, highlight repair.
3. **Recover** a linear DNG from that render, with SPP's tone curve and colour profiles embedded.
4. **Edit** in Camera Raw: it opens looking like SPP, with every Camera Raw control available, including extra highlight headroom.

About 5 seconds per file, or about 3.5 seconds per file when converting a batch two at a time.

## How close it is to SIGMA Photo Pro

Measured by rendering the DNG in Camera Raw and comparing it pixel by pixel with SPP's own output. ΔE is the median colour difference; values under about 1 are not visible.

| Test | Median ΔE | Notes |
|---|---:|---|
| Standard colour, default settings | 0.1 – 0.3 | Detail and noise match SPP (ratio 1.00) |
| White-balance presets, all 8 (9 shots) | 0.09 – 0.30 | Auto, Daylight, Shade, Overcast, Incandescent, Fluorescent, Flash, Custom |
| Monochrome | 0.10 – 0.40 | SPP's own black-and-white rendering |
| Fill Light +1 / +2 | 0.08 – 0.31 | Baked in at conversion |
| Noise reduction and sharpness extremes | 0.09 – 0.17 | Off/Max noise reduction, sharpness ±1 |
| Colour modes: Portrait, Neutral, Vivid, Landscape | 0.07 – 0.43 | Switchable profiles in Camera Raw |
| Colour mode: FOV Classic Blue | 0.35 – 1.26 | Less exact on very saturated colours |
| A file edited and saved in SPP | 0.70 | Outside near-white areas |

## Features

**The look**
- **SPP Standard by default** – the same colour, tone, noise reduction and sharpening SPP gives you out of the box.
- **All SPP colour modes as profiles** – Vivid, Neutral, Portrait, Landscape and FOV Classic Blue in Camera Raw's Profile menu, switchable without reconverting.
- **Monochrome mode** – SPP's Foveon black and white: its layer mix, monochrome noise reduction and tone curve. Opens in Camera Raw's Black & White mode.
- **White balance as shot** – every camera preset converts with SPP's colour matrix for that light, not just a temperature shift.
- **Your SPP edits** – files edited and saved in SPP convert with those edits: exposure, contrast, shadow, highlight, saturation, sharpness, fill light, noise reduction and colour mode.
- **Advanced settings** – Highlight Control (Neutralize to Restore), X3 Fill Light, Sharpness, and SPP's five-step Chroma and Luminance noise reduction.

**The workflow**
- **Double-click to Camera Raw** – double-click an X3F in Finder: it converts in the background and opens in Camera Raw, with no window.
- **Batch window** – drop files or folders, tick the ones you want and convert. Files with SPP edits are tagged.
- **Skips what is done** – already converted with the same settings? Skipped. Change a setting and it converts again.
- **Correct Finder previews** – thumbnails and Quick Look show the real look, not a flat, washed-out version.
- **Highlight headroom** – Camera Raw can still recover detail in highlights that SPP clips to white.
- **Compact files** – lossless compressed DNGs of about 54 MB, saved next to the original or in a folder you choose.

## Compared with other ways to open X3F files

| | X3FM Converter | SIGMA Photo Pro | Open-source X3F decoders | Generic raw editors |
|---|---|---|---|---|
| SPP's colour and detail | **Yes, from SPP's engine** | Yes | No, own colour science | No |
| Edit in Camera Raw and Photoshop | **Yes, full raw controls** | No | Partly, as a plain DNG | Yes |
| Colour modes, Monochrome, Fill Light | **Yes** | Yes | No | No |
| Reads edits saved in SPP | **Yes** | Yes | No | No |
| Highlights beyond SPP's white point | **Yes** | No | Varies | Varies |

## Getting started

1. Install **SIGMA Photo Pro 6** in your Applications folder if it isn't there already. The converter uses its engine and does not work without it.
2. Download `X3FM-Converter-1.7.1.zip` from Releases, unzip it and copy **X3FM Converter** and **X3FM to Camera Raw** into your Applications folder.
3. Open X3FM Converter with right-click › Open the first time. The apps are not signed by a registered Apple developer, so macOS asks once.
4. Click **Use for double-click** at the bottom of the window to make double-clicked X3F files open straight in Camera Raw.

**Good to know:** works with the DP Merrill cameras. SPP edits to monochrome settings, the tone-curve editor, crop and lens corrections are not read yet. Saving DNGs to a Mac folder is about twice as fast as writing them back to the SD card.

---

Not affiliated with or endorsed by SIGMA or Adobe. SIGMA Photo Pro, Foveon and Merrill belong to SIGMA; Camera Raw and Photoshop belong to Adobe.
