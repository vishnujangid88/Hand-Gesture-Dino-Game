# ✋ Hand Gesture Controlled Jump Trigger using OpenCV & ctypes

A Python-based real-time system that detects hand gestures using a webcam and triggers a **spacebar press** to simulate a jump (e.g., in a game) when a closed fist is detected. This tool is useful for creating interactive gesture-controlled applications or games.

---

## 📂 Project Structure

```

.
├── main.py        # Captures hand gestures and maps them to keyboard actions
├── keys.py        # Simulates key presses using Windows API

````

---

## 📽️ Demo

- ✊ Closed Fist → Simulates `SPACE` key press (Jump)
- 🖐️ Any other gesture → No action

---

## 📦 Requirements

- Python 3.7+
- Windows OS (due to `ctypes.windll` usage)
- Webcam
- Python libraries:
  - `opencv-python`
  - `cvzone`

Install with:

```bash
pip install opencv-python cvzone
````

---

## 🚀 How It Works

### `main.py`

* Uses **OpenCV** and **cvzone's HandTrackingModule** to detect hands and identify how many fingers are up.
* If **no fingers are up** (i.e., `[0, 0, 0, 0, 0]`), it sends a **spacebar key press** using functions from `keys.py`.
* Visual feedback is shown on the webcam feed (e.g., "Jumping...", "Finger count").

### `keys.py`

* Uses `ctypes` to interface with the Windows User32 API.
* Simulates key press and release actions via:

  * `PressKey(hexKeyCode)`
  * `ReleaseKey(hexKeyCode)`

The hex code for the spacebar (`0x39`) is used to simulate a jump.

---

## 🛠️ Usage

1. Ensure your webcam is connected.
2. Run the script:

```bash
python main.py
```

3. Make a **closed fist** → Character jumps (simulates SPACE).
4. Press **`q`** to exit.

---

## 🔑 Key Mappings

| Gesture           | Finger Code               | Action            |
| ----------------- | ------------------------- | ----------------- |
| ✊ Fist            | `[0, 0, 0, 0, 0]`         | Press `SPACE` key |
| ☝ One Finger      | `[0, 1, 0, 0, 0]`         | No Action         |
| ✌ Two Fingers     | `[0, 1, 1, 0, 0]`         | No Action         |
| 🖖 Three+ Fingers | `[0, 1, 1, 1, 0]` or more | No Action         |

---

## 📌 Notes

* Only works on **Windows** due to the use of `ctypes.windll`.
* You can modify `space_pressed` in `keys.py` to simulate other keys (e.g., arrow keys).
* Make sure your game or application is in focus for the simulated keypress to work.

---

## 📜 License

This project is released under the MIT License.

---

> Created for fun and experimentation with computer vision + keyboard automation 🔧🎮
