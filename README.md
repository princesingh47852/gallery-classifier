# Gallery Classifier

Automatically sorts your mixed phone photos into **Study Notes** and **Personal Photos** using AI (Transfer Learning with MobileNetV2).

---

## Folder Structure

```
gallery-classifier/
├── data/
│   ├── Study_Notes/       <- paste 20-25 notes photos here (for training only)
│   └── Personal_Photos/   <- paste 20-25 personal photos here (for training only)
├── my_photos/             <- paste your mixed photos here (for sorting)
├── sorted/                <- auto-created after running predict.py
│   ├── Study_Notes/
│   └── Personal_Photos/
├── train.py               <- run FIRST
├── predict.py             <- run SECOND
└── README.md
```

---

## Install Libraries

Open terminal in VS Code (`Ctrl+`\`) and run:

```
pip install tensorflow Pillow
```

---

## How to Use

### FIRST TIME — Train the model (do this once)

**Step 1** — Add training photos:
- Copy 20-25 notes/screenshots into `data/Study_Notes/`
- Copy 20-25 personal photos into `data/Personal_Photos/`

**Step 2** — Run train.py:
```
python train.py
```
Wait 3-5 minutes. When done, `model.h5` will appear in your folder.

---

### EVERY TIME AFTER — Sort any mixed folder

**Step 1** — Paste your mixed photos into the `my_photos/` folder

**Step 2** — Open `predict.py` and set your folder name:
```python
INPUT_FOLDER = 'my_photos'   # change this if your folder has a different name
```

**Step 3** — Run predict.py:
```
python predict.py
```

**Output:**
```
Scanning 'my_photos'...

  photo1.jpg       -> Study_Notes      (96.3%)
  photo2.jpg       -> Personal_Photos  (91.2%)
  photo3.jpg       -> Study_Notes      (88.7%)
  ...

Done! 42 photos sorted.
  Personal Photos -> sorted/Personal_Photos/  (18 photos)
  Study Notes     -> sorted/Study_Notes/      (24 photos)
```

Your sorted photos appear in the `sorted/` folder. Original photos are NOT deleted.

---

## What Goes Where

| Folder | Purpose | You put photos here |
|---|---|---|
| `data/Study_Notes/` | Training data | Once only (20-25 photos) |
| `data/Personal_Photos/` | Training data | Once only (20-25 photos) |
| `my_photos/` | Input for sorting | Every time you want to sort |
| `sorted/` | Sorted output | Auto-created by predict.py |

---

## How It Works

Uses **Transfer Learning** — MobileNetV2 is already trained on 1.2 million images from ImageNet. It already knows how to detect edges, textures, and shapes. We add one small layer on top and train it on our 40-50 photos to learn the difference between notes and personal photos.

| Feature | Study Notes | Personal Photos |
|---|---|---|
| Colors | Black and white, high contrast | Colorful, diverse |
| Edges | Sharp (text lines) | Soft (faces, nature) |
| Texture | Structured, uniform | Random, organic |

---

## Files on GitHub

Upload only these files to GitHub:
```
train.py
predict.py
README.md
```

Do NOT upload `data/`, `my_photos/`, `sorted/`, or `model.h5` — they contain your personal photos and are too large.

---

## Someone Else Running Your Project

1. Download ZIP from GitHub
2. Open in VS Code
3. Run `pip install tensorflow Pillow`
4. Add their own photos to `data/Study_Notes/` and `data/Personal_Photos/`
5. Run `python train.py` — trains on their photos
6. Add mixed photos to `my_photos/`
7. Run `python predict.py` — sorts their photos

The model trains fresh each time because everyone's photos are different.

---

*Module 5 Project — Transfer Learning | First Year AI/ML*
