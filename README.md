# **Optimizing NSFW Content Detection Using Quantization Techniques**

## Team Members:

1. [Pavan Pandya](mailto:pnpandya@iu.edu)
2. [Harsh Shah](mailto:shahhh@iu.edu)
3. [Dhruvil Dholariya](mailto:ddholari@iu.edu)
4. [Dev Patel](mailto:dp67@iu.edu)

---

## Repository Overview

This project explores the development of a robust and efficient deep learning-based classifier for **Not Safe For Work (NSFW)** content detection. The focus is on expanding the classification scope to include additional categories (nudity, drugs, violence, and gore) and enhancing the efficiency of the model using quantization techniques. The quantized model achieves significant improvements in inference speed and size reduction while maintaining high accuracy.

---

## **Table of Contents**

1. [Introduction](#1-introduction)
2. [Features](#2-features)
3. [Technologies Used](#3-technologies-used)
4. [Workflow](#4-workflow)
5. [Experiments and Results](#5-experiments-and-results)
6. [Future Work](#6-future-work)
7. [Acknowledgments](#7-acknowledgments)

---

## **1. Introduction**

The rise of digital content-sharing platforms has brought challenges in moderating user-generated content, especially for detecting **NSFW material**. Current solutions face trade-offs between accuracy and computational efficiency. This project aims to:

1. **Expand NSFW Classification Scope**: Beyond nudity, it includes categories like **drugs**, **violence**, and **gore**.
2. **Optimize Deep Learning Models**: Using **quantization techniques** like **Quantization-Aware Training (QAT)** and **Post-Training Quantization (PTQ)** for better inference speed and smaller model size.

---

## **2. Features**

1. **Comprehensive Classification**:
   - Detects NSFW categories: **Nudity**, **Drugs**, **Violence**, **Gore**, and **Safe Content**.
2. **Efficient Inference**:
   - Model size reduced by **75%**.
   - Inference latency decreased by up to **57%** on CPU.
3. **High Accuracy**:
   - Achieved **95.1% accuracy** with Quantization-Aware Training (QAT).
4. **Real-Time Suitability**:
   - Optimized for deployment on resource-constrained environments like mobile devices.

---

## **3. Technologies Used**

- **Frameworks**: PyTorch
- **Models**: ResNet18 (Pre-trained on ImageNet)
- **Optimization Techniques**:
  - Quantization-Aware Training (QAT)
  - Post-Training Quantization (PTQ)
- **Datasets**:
  - **Roboflow** for drugs [[1]](#7-acknowledgments) and gore [[2]](#7-acknowledgments)
  - **NudeNet** for nudity [[3]](#7-acknowledgments)
  - **Kaggle** for violence [[4]](#7-acknowledgments)
  - **NudeNet** and **Kaggle** for safe [[3]](#7-acknowledgments) [[4]](#7-acknowledgments)

---

## **4. Workflow**

### **Step 1: Dataset Preparation**

- Curated a dataset with **39,976 images** spanning 5 categories: nudity, drugs, gore, violence, and safe content.
- Preprocessing steps included:
  - Resizing images to **320x320 pixels**.
  - Standardizing to RGB format.
  - Implementing a custom PyTorch dataloader for efficient training.

### **Step 2: Model Development**

- **Baseline Model**: Customized **ResNet18** for multi-class classification.
  - Modified classification head with:
    - A linear layer (512 units).
    - ReLU activation and dropout.
    - Final output layer for 5 categories.

### **Step 3: Quantization Techniques**

- **Post-Training Quantization (PTQ)**:
  - Reduced model precision to 8-bit integers.
  - Achieved **93.83% accuracy** with a significant reduction in size and latency.
- **Quantization-Aware Training (QAT)**:
  - Incorporated quantization during training.
  - Achieved **95.10% accuracy**, improving upon the baseline.

### **Step 4: Evaluation**

- Evaluated models for accuracy, latency, and size:
  - **Baseline ResNet18**: 94.10% accuracy, 51.22ms latency (CPU), 45.85MB size.
  - **PTQ**: 93.83% accuracy, 19.84ms latency (CPU), 11.49MB size.
  - **QAT**: 95.10% accuracy, 22.18ms latency (CPU), 11.49MB size.

---

## **5. Experiments and Results**

### **Results Summary**

| Model Version            | Test Accuracy (%) | Model Size (MB) | Latency (ms/sample) (CPU) |
| ------------------------ | ----------------- | --------------- | ------------------------- |
| Baseline ResNet18        | 94.10             | 45.85           | 51.22                     |
| Post-Training (PTQ)      | 93.83             | 11.49           | 19.84                     |
| Quantization-Aware (QAT) | 95.10             | 11.49           | 22.18                     |

### **Key Insights**

1. **QAT** achieved the highest accuracy (95.10%) with faster inference times compared to the baseline model.
2. **PTQ** offers a lightweight alternative with minimal accuracy loss, making it ideal for deployment in resource-constrained environments.

---

## **6. Future Work**

- Expand Categories: Include more nuanced NSFW classifications.
- Incorporate Advanced Quantization: Explore mixed-precision quantization and Vision Transformers.
- Automated Parameter Tuning: Develop tools for optimizing quantization parameters dynamically.

## **7. Acknowledgments**

1. Roboflow. Drugs dataset. [Website Link](https://universe.roboflow.com/cbait/drugs_newest/dataset/2)
2. Roboflow. Gore dataset. [Website Link](https://universe.roboflow.com/computer-vision-y8bhq/sensitive-content-2/dataset/1)
3. Bedapudi Praneeth. Nudenet. [Website Link](https://academictorrents.com/details/1cda9427784a6b77809f657e772814dc766b69f5)
4. Mohamed Elesawy Mohamad Hussein Mina Abd El Massih. Violence dataset. [Website Link](https://www.kaggle.com/datasets/mohamedmustafa/real-life-violence-situations-dataset)
