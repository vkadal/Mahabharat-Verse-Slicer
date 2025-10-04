# Mahabharat-Verse-Slicer

A compact toolkit to turn **one long PDF** into **individual verse images**.

### Tools
1. **pdf_to_pages.py** — split a PDF into per-page images (PNG/JPG/TIFF/WEBP)
2. **crop_margins_images.py** — trim all outer margins from those page images
3. **separate_verses.py** — detect horizontal whitespace and slice pages into verse tiles

> Developed collaboratively with the help of **ChatGPT (OpenAI)**.

---

## Install

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

---

## Usage

### 1) PDF → pages
```bash
python3 pdf_to_pages.py Mahabharat-Adhi-Parva.pdf out/pages --dpi 220 --ext png
```

### 2) Trim margins (all sides)
```bash
python3 crop_margins_images.py --input out/pages --outdir out/pages_cropped --bin-thresh 180 --pad 6
```

### 3) Slice into verse tiles
```bash
python3 separate_verses.py --input out/pages_cropped --outdir out/verses --min-gap 12 --pad 6
```

Output:
```
out/verses/
  page-001/
    verse-001.png
    verse-002.png
    ...
  page-002/
    verse-001.png
    ...
```

### Tips
- Increase `--dpi` in step 1 for small/low-contrast text.
- If pages are very faint, raise `--bin-thresh 200` in steps 2 and 3.
- Tweak `--min-gap` (10–20) if verses are tightly spaced.

---

## .gitignore

This repository includes a `.gitignore` file.

It tells Git which files **not** to upload to GitHub, such as:

- Python cache files (`__pycache__/`, `*.pyc`, …)
- Local virtual environments (`venv/`, `.venv/`)
- Generated outputs (`out/`, `*.png`, `*.jpg`, …)
- OS junk files (`.DS_Store`, `Thumbs.db`)

This keeps the repo **clean**: only scripts and documentation are tracked.

---

## License & Disclaimer

**License:** MIT (see `LICENSE`).

**Disclaimer:** Provided “as is,” without warranty. Designed for Mahābhārata scans but should generalize; tune thresholds for your material.

**Acknowledgment:** These scripts were developed with the help of **ChatGPT (OpenAI)**.
