# DIPT_EX_05_Record-Implementation-of-Filters

# Name : TAMIZHSELVAN B

# Reg.No : 212223230225

## Aim
To implement filters for smoothing and sharpening images in the spatial domain using Python and OpenCV.

## Software Required
1. Anaconda – Python 3.7
2. OpenCV library
3. NumPy library

## Algorithm
### Step 1:
Import necessary libraries like cv2 and numpy for image processing.

### Step 2:
Read the input image using cv2.imread() and convert it to grayscale if required.

### Step 3:
Apply smoothing filters such as Averaging, Weighted Averaging, Gaussian, and Median filters to reduce image noise and enhance smoothness.

### Step 4:
Apply sharpening filters using Laplacian Kernel and Laplacian Operator to highlight edges and fine details in the image.

### Step 5:
Display all filtered images using cv2.imshow() and close all OpenCV windows using cv2.destroyAllWindows().


 ## PROGRAM : 


 ```py

import cv2
import numpy as np
import matplotlib.pyplot as plt
# Syntex 
# dst = cv2.filter2D(src, ddepth, kernel[, dst[, anchor[, delta[, borderType]]]])
# Define a Kernel
kernel = np.ones((5,5), dtype = np.float32) / 5**2
print (kernel)
# To Perform Convolution 
image = cv2.imread('dog.jpg')

dst = cv2.filter2D(image, ddepth = -1, kernel = kernel)
plt.axis('off')
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.show()
plt.axis('off')
plt.imshow(dst[:,:,::-1])
plt.title("Convolution Result")
plt.show()


# Syntex 
# dst = cv2.blur(src, ksize[, dst[, anchor[, borderType]]])
average_filter = cv2.blur(image, (30,30))
# Display the images.
plt.imshow(image [:, :, ::-1])
plt.title('Input Image')
plt.show()
plt.imshow(average_filter[:, :, ::-1])
plt.title('Output Image ( Average Filter)')


# Syntex 
# dst = cv2.GaussianBlur(src, ksize, sigmaX[, dst[, sigmaY[, borderType]]])
kernel = np.array([[1,2,1],
                   [2,4,2],
                   [1,2,1]])/16
weighted_average_filter = cv2.filter2D(image, -1, kernel)
# Display the images.
plt.imshow(image [:, :, ::-1])
plt.title('Input Image')
plt.show()
plt.imshow(weighted_average_filter[:, :, ::-1])
plt.title('Output Image(weighted_average_filter)')
plt.show()


# Apply Gaussian blur.
gaussian_filter = cv2.GaussianBlur(image, (29,29), 0, 0)
# Display the images.
plt.imshow(image [:, :, ::-1])
plt.title('Input Image')
plt.show()
plt.imshow(gaussian_filter[:, :, ::-1])
plt.title('Output Image ( Gaussian Filter)')
plt.show()


# iv) Using Median Filter
median_filter = cv2.medianBlur(image, 19)
# Display the images.
plt.imshow(image [:, :, ::-1])
plt.title('Input Image')
plt.show()
plt.imshow(median_filter[:, :, ::-1])
plt.title('Output Image ( Median_filter)')
plt.show()


# i) Using Laplacian Kernel (Manual Kernel)
laplacian_kernel = np.array([[0, -1, 0],
                             [-1, 5, -1],
                             [0, -1, 0]])
sharpened_laplacian_kernel = cv2.filter2D(image, -1, kernel = laplacian_kernel)
# Display the images.
plt.imshow(image [:, :, ::-1])
plt.title('Input Image')
plt.show()
plt.imshow(sharpened_laplacian_kernel[:, :, ::-1])
plt.title('Output Image ( Laplacian_filter)')


# ii) Using Laplacian Operator (OpenCV built-in)
gray_image = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)
laplacian_operator = cv2.Laplacian(gray_image, cv2.CV_64F)
laplacian_operator = np.uint8(np.absolute(laplacian_operator))
# Display the images.
plt.imshow(image [:, :, ::-1])
plt.title('Input Image')
plt.show()
plt.imshow(gray_image, cmap='gray') 
plt.title('Gray_image')
plt.show()
plt.imshow(laplacian_operator,cmap='gray')
plt.title('Output Image ( Laplacian_filter)')


```

## OUTPUT :

### Convolution in OpenCV :
<img width="277" height="282" alt="image" src="https://github.com/user-attachments/assets/ff690d05-a60c-4f39-94b2-9ddc78bcee64" />


### Convolution :
<img width="261" height="278" alt="image" src="https://github.com/user-attachments/assets/dcc810d2-e78b-494a-bf8a-4a7fc1a9b1f6" />


## Smoothing filter :
### Averaging Filter :
<img width="252" height="575" alt="image" src="https://github.com/user-attachments/assets/ef7759dc-ee4a-4984-9731-08e6cf74a0bc" />


### Weighted Averaging Filter (custom kernel) :
<img width="272" height="562" alt="image" src="https://github.com/user-attachments/assets/25fba579-2f60-4c2d-9673-ad189ef7cac7" />


### Gaussian Filter :
<img width="275" height="565" alt="image" src="https://github.com/user-attachments/assets/7e3e9e1c-7a16-4c73-8f60-f62076578b1f" />


### Median Filter :
<img width="257" height="565" alt="image" src="https://github.com/user-attachments/assets/9b9efe83-7213-476a-8625-baa0a92f8f10" />



## Sharpening Filters :
### Laplacian Kernel (Manual Kernel) :
<img width="372" height="766" alt="image" src="https://github.com/user-attachments/assets/dfc5be59-61c9-4c07-a0ba-c8744c781c54" />



### Laplacian Operator (OpenCV built-in) :
<img width="272" height="850" alt="image" src="https://github.com/user-attachments/assets/91a81f2c-dd97-4915-8346-0e2e7cf45248" />



## RESULT:

Thus, we successfully implemented filters for smoothing and sharpening images in the spatial domain using Python and OpenCV.








