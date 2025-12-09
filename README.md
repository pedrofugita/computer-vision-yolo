# Real-Time Object Detection Pipeline using YOLOv8

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![YOLOv8](https://img.shields.io/badge/Model-YOLOv8-green?style=for-the-badge)
![OpenCV](https://img.shields.io/badge/Library-OpenCV-red?style=for-the-badge&logo=opencv&logoColor=white)
![Status](https://img.shields.io/badge/Status-PoC-orange?style=for-the-badge)

## 📌 Project Overview
This project consists of a computer vision pipeline developed to perform **real-time object detection** in video streams. Leveraging the power of the **YOLOv8 (You Only Look Once)** architecture, the system is capable of identifying and classifying objects with high inference speed and accuracy.

This implementation serves as a **Proof of Concept (PoC)** for automated monitoring systems, applicable in scenarios such as industrial safety, pedestrian traffic analysis, and perimeter surveillance.

---

## ⚙️ The Problem & Solution
**The Challenge:**
Manual monitoring of video footage for security or operational metrics (like counting people or vehicles) is inefficient, prone to human error, and not scalable for large operations.

**The Solution:**
An automated detection system that:
1.  **Ingests** raw video footage.
2.  **Processes** frames using a pre-trained Neural Network (YOLOv8 Nano).
3.  **Outputs** visual analytics with bounding boxes and class confidence scores in real-time.

---

## 🚀 Key Features
* **SOTA Architecture:** Utilizes Ultralytics YOLOv8 for optimal speed/accuracy trade-off.
* **Video Inference:** Capable of processing `.mp4` streams frame-by-frame.
* **Confidence Thresholding:** Configured with a `0.5` confidence score to filter out false positives, ensuring cleaner detection results.
* **Cloud Integration:** Developed using Google Colab with Google Drive mounting for efficient data handling.

---

## 🛠️ Tech Stack
* **Language:** Python
* **Core Library:** `ultralytics` (YOLOv8)
* **Image Processing:** OpenCV (`cv2`)
* **Environment:** Jupyter Notebook / Google Colab

---

## 📊 How It Works (Logic)
The script follows a standard ETL (Extract, Transform, Load) pattern for unstructured data:

1.  **Environment Setup:** Installs dependencies and mounts cloud storage.
2.  **Model Loading:** Initializes the `yolov8n.pt` (Nano) weights for lightweight processing.
3.  **Inference Loop:** Runs the prediction method on the source video with `show=True` to visualize results in real-time.

### Core Logic Snippet
```python
from ultralytics import YOLO

# Load the model (Nano version for speed)
model = YOLO("yolov8n.pt")

# Run inference on video source
# conf=0.5 ensures only detections with >50% confidence are shown
results = model.predict(source='video_path.mp4', show=True, conf=0.5)

📈 Potential Applications
Although implemented as a study, this logic is the foundation for:

Retail: Counting customers in a store to analyze peak hours.

Industry 4.0: Detecting workers entering dangerous zones (Safety).

Smart Cities: Traffic flow analysis and congestion detection.

🔜 Future Improvements
[ ] Implement a counter to track the total number of unique objects.

[ ] Export detection data (timestamps and classes) to a SQL database.

[ ] Deploy the model to an edge device (e.g., Raspberry Pi) for on-site processing
