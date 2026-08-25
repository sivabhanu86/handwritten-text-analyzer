# Handwritten English Character Recognition

A progressive computer vision and machine learning project for recognizing handwritten English characters from images.

The project explores multiple approaches, starting with traditional image-processing techniques and gradually moving toward machine learning and deep learning.

## Project Progress

### Level 1 — Character Segmentation and Template Matching

**Approach:** OpenCV + Pixel-based Template Matching

The first stage focused on understanding the fundamentals of character recognition.

#### Pipeline

```text
Input Image
    ↓
Grayscale Conversion
    ↓
Binary Thresholding
    ↓
Contour Detection
    ↓
Character Segmentation
    ↓
Character Cropping
    ↓
64 × 64 Resizing
    ↓
Template Comparison
    ↓
Character Recognition
```

The method successfully recognized text when the input characters were generated using the same font as the templates.

**Example:**

```text
Input:  HELLO WORLD
Output: HELLOWORLD
```

#### Limitation

The approach depends heavily on the visual similarity between the input character and the stored template. Therefore, it performs well under controlled conditions but does not generalize reliably to different handwriting styles.

---

### Level 2 — Contour-Based Shape Matching

**Approach:** OpenCV Contours + Shape Matching

The second stage explored whether character recognition could be performed based on the shape of characters rather than direct pixel comparison.

#### Pipeline

```text
Input Character
    ↓
Grayscale
    ↓
Thresholding
    ↓
Contour Detection
    ↓
Contour Extraction
    ↓
Shape Comparison
    ↓
Character Prediction
```

OpenCV's `matchShapes()` method was used to compare the contours of input characters with template contours.

#### Result

The method showed that contour-based shape similarity alone was not sufficiently reliable for handwritten character recognition.

For example, visually similar handwritten characters could produce misleading contour similarities, resulting in incorrect predictions such as an `H` being recognized as an `X`.

#### Conclusion

Contour geometry captures the overall shape of a character but does not sufficiently represent the variations present in handwritten characters.

---

### Level 3 — Machine Learning-Based Character Recognition

**Approach:** OpenCV + Scikit-learn + KNN + SVM

The third stage moved from manually comparing characters to training machine learning models using a handwritten English character dataset.

#### Dataset

A handwritten English alphabet dataset containing character images organized into training, testing, and validation sets was used.

The dataset is not included in this repository because of its size.

#### Preprocessing

```text
Input Image
    ↓
Grayscale Conversion
    ↓
Thresholding
    ↓
Character Segmentation
    ↓
Cropping
    ↓
Resizing
    ↓
Feature Extraction
    ↓
Machine Learning Model
```

OpenCV was used for image preprocessing and feature extraction.

The processed character images were converted into numerical feature vectors and supplied to machine learning classifiers.

#### Models Evaluated

* K-Nearest Neighbors (KNN)
* Support Vector Machine (SVM)

Both models were evaluated using the same dataset and preprocessing pipeline.

### Model Comparison

The SVM model performed better than KNN in the experiments conducted on the handwritten character dataset.

This stage demonstrated the advantage of learning character patterns from multiple training examples rather than relying directly on individual templates or manually comparing character shapes.

---

## Technologies Used

* **Python**
* **OpenCV**
* **NumPy**
* **Matplotlib**
* **Scikit-learn**
* **Jupyter Notebook**
* **Git & GitHub**

## Project Structure

```text
handwritten-text-analyzer/
│
├── level_1_character_segmentation_and_template_matching/
│   └── notebooks/
│
├── level_2_contour_based_shape_matching/
│   └── notebooks/
│
├── level_3_machine_learning_based_character_recognition/
│   └── notebooks/
│
├── level_4_cnn_based_character_recognition/
│   └── notebooks/
│
├── .gitignore
└── README.md
```

## Learning Progression

The project is intentionally developed in multiple stages:

```text
Template Matching
       ↓
Contour-Based Shape Matching
       ↓
Traditional Machine Learning
       ↓
Deep Learning
```

Each level was used to understand the limitations of the previous approach and identify why a more advanced method is required.

## Future Work

### Level 4 — CNN-Based Character Recognition

The next stage will use a Convolutional Neural Network (CNN) to learn visual features directly from handwritten character images.

Planned work includes:

* CNN architecture development
* Training and validation
* Performance comparison with KNN and SVM
* Confusion matrix analysis
* Testing on unseen handwritten characters
* Evaluation of the complete character-recognition pipeline

## Dataset

The handwritten character dataset is kept outside this repository because of its size.
The dataset source and download information will be provided separately.

## Current Status

| Level   | Approach                     | Status      |
| ------- | ---------------------------- | ----------- |
| Level 1 | Template Matching            | Completed   |
| Level 2 | Contour-Based Shape Matching | Completed   |
| Level 3 | KNN & SVM                    | Completed   |
| Level 4 | CNN                          | In Progress |
