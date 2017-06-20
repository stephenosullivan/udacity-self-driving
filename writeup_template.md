# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidYellowCurve.jpg "SolidYellowCurve"
[image2]: ./test_images_output/solidWhiteCurve.jpg "SolidWhiteCurve"
---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps: 
- Grayscale
- GaussianBlur
- Canny
- Construct Hough lines over the lane boundary
- Combine Hough lines over the original background image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by taking the point pairs from the HoughLines function and assigned them to either the left or right lane boundary depending on the slope of the respective Hough line. I then fitted a line to each of these sets of points using linear regression. I also have functionality to restrict the length of these two lines by using the Hough line point with the minimum y value as an upper vertical bound and use the screen size as a lower vertical bound.
 

![The dots over each line are indicating Hough line points assigned to the left the right lanes][image1]


### 2. Identify potential shortcomings with your current pipeline

The pipeline seems to be very sensitive to the HoughLine parameters


### 3. Suggest possible improvements to your pipeline

For the challenge part of the project the general system does not seem to be very robust. For instance some road repair is enough to throw off my draw_lines() function
