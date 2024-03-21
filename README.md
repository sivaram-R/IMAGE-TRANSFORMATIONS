# EX-4 IMAGE TRANSFORMATIONS


## Aim
To perform image transformation such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping using OpenCV and Python.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import necessary libraries (NumPy, OpenCV, Matplotlib).
<br>

### Step2:
Read an image, convert it to RGB format, and display it using Matplotlib.Define translation parameters 
(e.g., shifting by 100 pixels horizontally and 200 pixels vertically).Perform translation using cv2.warpAffine().
Display the translated image using Matplotlib.
<br>

### Step3:
Obtain the dimensions (rows, cols, dim) of the input image.
Define a scaling matrix M with scaling factors of 1.5 in the x-direction and 1.8 in the y-direction
.Perform perspective transformation using cv2.warpPerspective(), scaling the image by a factor of 1.5 in the x-direction and 1.8 in the y-direction.
Display the scaled image using Matplotlib.
<br>

### Step4:
Define shear matrices M_x and M_y for shearing along the x-axis and y-axis, respectively.
Perform perspective transformation using cv2.warpPerspective() with the shear matrices to shear the image along the x-axis and y-axis.
Display the sheared images along the x-axis and y-axis using Matplotlib.
<br>

### Step5:
Define reflection matrices M_x and M_y for reflection along the x-axis and y-axis, respectively.
Perform perspective transformation using cv2.warpPerspective() with the reflection matrices to reflect the image along the x-axis and y-axis.
Display the reflected images along the x-axis and y-axis using Matplotlib.
<br>

### Step 6 :
Define an angle of rotation in radians (here, 10 degrees).
Construct a rotation matrix M using the sine and cosine of the angle.
Perform perspective transformation using cv2.warpPerspective() with the rotation matrix to rotate the image.Display the rotated image using Matplotlib.
<br>
### Step 7 :
Define a region of interest by specifying the desired range of rows and columns to crop the image (here, from row 100 to row 300 and from column 100 to column 300).
Use array slicing to extract the cropped region from the input image.Display the cropped image using Matplotlib.
<br>


## Program:
```

#### Developed By: Sivaram R
#### Register Number: 212222100050
```
<table>
  <tr>
   <td width=50%>
     
### i)Image Translation
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tree.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()
rows,cols,dim=input_image.shape
M = np.float32([[1, 0, 100],[0, 1, 200],[0, 0, 1]])

translated_image = cv2.warpPerspective(input_image, M, (cols, rows))
plt.axis('off')
plt.imshow(translated_image)
plt.show()
```
</td>
<td>
  
### Output:
### i)Image Translation
![1](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/d05be5ed-7537-4841-9e5b-87a5d90b5aef)
![2](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/fc4457bb-12e9-4e45-9e6d-4689e86e4b58)
</td>
</tr>



<tr>
  <td width=50%>
  
### ii) Image Scaling
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tree.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

rows, cols, dim = input_image.shape 
M = np.float32([[1.5, 0, 0],[0, 1.8, 0],[0, 0, 1]])

scaled_img=cv2.warpPerspective (input_image, M, (cols*2, rows*2))
plt.imshow(scaled_img)
plt.show()
```
</td>
<td>
  
### Output:
### ii) Image Scaling
![3](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/a47160b1-14c7-460a-a54f-acf02f07eb7d)
![4](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/7821a125-c2cd-4d3e-9b4b-9218d7eae95c)
</td>
</tr>

<tr>
  <td width=50%>

### iii)Image shearing
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tree.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

M_x = np.float32([[1, 0.5, 0],[0, 1 ,0],[0,0,1]])
M_y =np.float32([[1, 0, 0],[0.5, 1, 0],[0, 0, 1]])

sheared_img_xaxis=cv2.warpPerspective(input_image,M_x, (int(cols*1.5), int(rows *1.5)))
sheared_img_yaxis = cv2.warpPerspective(input_image,M_y,(int(cols*1.5), int(rows*1.5)))

plt.imshow(sheared_img_xaxis)
plt.show()

plt.imshow(sheared_img_yaxis)
plt.show()
```
</td>
<td>
  
### Output:
### iii)Image shearing
![3](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/510cc2e9-5492-4094-a80d-7832378c11cc)
![5](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/108dc9f4-083f-4010-991c-738e26e6e076)
![6](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/87ed521c-bf08-4afd-92ef-055dd8e252e5)
</td>
</tr>



<tr>
  <td width=50%>

### iv)Image Reflection
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tree.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

M_x= np.float32([[1,0, 0],[0, -1, rows],[0, 0, 1]])
M_y =np.float32([[-1, 0, cols],[ 0, 1, 0 ],[ 0, 0, 1 ]])
# Apply a perspective transformation to the image
reflected_img_xaxis=cv2.warpPerspective (input_image, M_x,(int(cols), int(rows)))
reflected_img_yaxis= cv2.warpPerspective (input_image, M_y, (int(cols), int(rows)))

                                         
plt.imshow(reflected_img_xaxis)
plt.show()

plt.imshow(reflected_img_yaxis)
plt.show()
```
</td>
<td>

### Output:
### iv)Image Reflection
![3](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/9a19e2d2-fd74-47fe-b666-75b8796ca0f0)
![7](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/591c1fa0-5a1b-4212-bc54-0ef3a9875db6)
![8](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/19e4064f-2ce1-4497-9365-1511ee081091)
</td>
</tr>



<tr>
 <td width=50%>

   ### v)Image Rotation
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tree.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

angle=np.radians(10)
M=np.float32([[np.cos(angle),-(np.sin(angle)),0],[np.sin(angle),np.cos(angle),0],[0,0,1]])
rotated_img = cv2.warpPerspective(input_image,M,(int(cols),int(rows)))

plt.imshow(rotated_img)
plt.show()
```
</td>
<td>
  
### Output:
### v)Image Rotation
![3](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/76d6dcc1-6931-4ef9-a38f-8c2cade91bbc)
![9](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/f22dc0f7-f16e-47be-8cb4-dedaf86c4758)
</td>
</tr>



<tr>
 <td width=50%>

### vi)Image Cropping
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
input_image = cv2.imread("tree.jpg")
input_image = cv2.cvtColor(input_image,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(input_image)
plt.show()

cropped_img= input_image[100:300,100:300]

plt.imshow(cropped_img)
plt.show()
```
</td>
<td>
  
### Output:
### vi)Image Cropping
![3](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/4c27db89-e7e6-40c0-85b0-c1fde1852f83)
![10](https://github.com/sivaram-R/IMAGE-TRANSFORMATIONS/assets/121165794/c44cb557-916b-4924-8882-8e0cc6b9c230)
</td>
</tr>
</table>

### Result: 

Thus the different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping are done using OpenCV and python programming.
