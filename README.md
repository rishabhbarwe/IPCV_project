🌿 Crop Disease Detection Using Deep Learning

A two-stage deep learning system for detecting crop species and identifying diseases using transfer learning (MobileNetV2 + InceptionV3). This project is implemented in Google Colab and trained using the multi-crop leaf dataset.

🚀 Project Overview

Crop diseases significantly affect agricultural productivity and farmer income. Traditional manual inspection is slow, subjective, and requires expertise.
This project uses deep learning and transfer learning to automate crop disease detection, making it fast, accurate, and scalable.

The system uses a two-stage classification pipeline:

Stage 1 — Crop Classification
Model: MobileNetV2
Input: Leaf image
Output: Detected crop type (e.g., Banana, Chilli, Radish, etc.)

Stage 2 — Disease Classification
Model: InceptionV3
Separate model for each crop
Input: Same leaf image

Output: Disease label (e.g., Healthy, Leaf Spot, Sigatoka)
This design improves accuracy and ensures each crop is handled by a specialized disease classifier.

Crop Classification
Dataset/
 └── crop/
       ├── Corn/
       ├── Rice/
       ├── Cashew/
       ├── Potato/
       └── Tomato/
       
Disease Classification  
Dataset/
 └── disease/
       ├── Corn/
       │     ├── Healthy/
       │     ├── Disease1/
       │     └── Disease2/
       ├── Rice/
       ├── Cashew/
       ├── Potato/
       └── Tomato/
       
🧠 Model Architecture
Model 1: MobileNetV2
Role: Crop classification

Model 2: InceptionV3
Role: Disease classification

🔧 Preprocessing
To improve training stability, each image is:
Resized to 224×224
Normalized to range [0,1]
Augmented with rotation, shifts, and flips
(⚠️ Segmentation was removed because it caused black images)

Training
To train models, run the Colab notebook:

history_crop = model_crop.fit(...)
history_disease = model_disease.fit(...)

Each model trains for 10 epochs using:
Adam optimizer
categorical_crossentropy
ImageDataGenerator with augmentation
80/20 train-validation split

🧪 Testing the Model
Prediction pipeline:
Preprocess input image
Predict crop using MobileNetV2
Load corresponding disease model
Predict disease
Return final result

📦 Installation
Clone the repository:
git clone https://github.com/rishabhbarwe/IPCV_project.git

Install dependencies: 
pip install tensorflow opencv-python matplotlib numpy


📚 Citation
Dataset Source:
Kumar, P. et al. (2025). Multi-Crop Leaf Disease Dataset. Mendeley Data. 
link - https://data.mendeley.com/datasets/z6jp232g5j/1

Transfer Learning Models Used:
Howard, A. G., et al. MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications. 2017.
Szegedy, C., et al. Rethinking the Inception Architecture for Computer Vision. 2016.


Plant Disease Classification Reference:
Mohanty, S.P., Hughes, D.P., & Salathé, M. (2016). Using Deep Learning for Image-Based
link - https://www.frontiersin.org/journals/plant-science/articles/10.3389/fpls.2016.01419/full

Original Research Paper:
link - https://ieeexplore.ieee.org/stampPDF/getPDF.jsp?tp=&arnumber=8697390&ref=aHR0cHM6Ly9zY2hvbGFyLmdvb2dsZS5jb20v&tag=1
