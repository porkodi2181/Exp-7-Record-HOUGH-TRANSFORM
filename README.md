# Hough Transform for Line Detection Using OpenCV

## NAME:  PORKODI B 
## REG NO: 212224240114

## Aim

To detect straight lines in an input image using the Probabilistic Hough Transform technique with OpenCV and Python.

## Software Requirements

- Python
- Anaconda
- Jupyter Notebook
- OpenCV
- NumPy
- Matplotlib

## Hough Transform

The Hough Transform is a feature extraction technique used in digital image processing to detect straight lines in an image.

The Probabilistic Hough Transform detects line segments from an edge-detected image. In this experiment, Canny Edge Detection is used to identify edges, and HoughLinesP() is used to detect straight lines.

## Algorithm

1. Import the required libraries: OpenCV, NumPy, and Matplotlib.
2. Read the input image using `cv2.imread()`.
3. Convert the input image into grayscale using `cv2.cvtColor()`.
4. Display the original image.
5. Apply Canny Edge Detection using `cv2.Canny()`.
6. Detect line coordinates using `cv2.HoughLinesP()`.
7. Extract the starting and ending coordinates of the detected lines.
8. Draw the detected lines on the original image using `cv2.line()`.
9. Display the final image with detected lines.

## Implementation

### 1. Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Read and Convert the Image

```python
image = cv2.imread('Image.png')

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

### 3. Display Original Image

```python
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Input Image")
plt.axis('off')
```

**OUTPUT:**

<img width="366" height="452" alt="image" src="https://github.com/user-attachments/assets/2488e332-fedc-4961-bd7c-471d08ad47e2" />

### 4. Grayscale Image

```python
plt.imshow(gray_image, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
```

**OUTPUT:**

<img width="381" height="452" alt="image" src="https://github.com/user-attachments/assets/1a29f6ed-7dee-4854-9b75-e13f57d24bf3" />


### 5. Canny Edge Detection

```python
edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(edges, cmap='gray')
plt.title("Canny Edge Detector")
plt.axis('off')
```

**OUTPUT:**

<img width="421" height="475" alt="image" src="https://github.com/user-attachments/assets/29a1b5d8-5efa-4d5f-9366-f7aca3644817" />

### 6. Hough Transform for Line Detection

```python
lines = cv2.HoughLinesP(
    edges,
    1,
    np.pi / 180,
    100,
    minLineLength=50,
    maxLineGap=10
)
```

### 7. Draw the Detected Lines

```python
if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(image, (x1, y1), (x2, y2),
                 (0, 255, 0), 2)
```

### 8. Display the Result of Hough Transform

```python
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Result of Hough Transform")
plt.axis('off')
```

**OUTPUT:**

<img width="382" height="453" alt="image" src="https://github.com/user-attachments/assets/22804820-cb77-4123-ab4f-2bc77f27a84b" />


## Result

Thus, straight lines in the input image were successfully detected using the Probabilistic Hough Transform technique with OpenCV and Python.
