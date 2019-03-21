# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a guassian blur with a kernel size of 11. Canny edge detection was then applied to the blurred image with low threshold of 40 and a highthreshold of 50. A region of interest was then defined using vertices that were tuned through trial and error. Finally the edge image was passed through a hough transform.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first separating the lines into left and right lines using their slopes (Negative slopes for righ lines and positive slopes for left lines). The slopes of the left and right lines were calcuated and averaged. Lines were then fit on the points corresponding to the the left and right lines using the 'fitLine()' method and intercepts and sslopes of these 2 lines calculated. USing the equation x = (y - b)/m, x points for the lines are calcualted and then two lines are then drawn on the image. 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


My current pipeline doesn't work well with winding lane lines and on roads with changing conditions(e.g shadows and color pathces)


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to average the detected lines over previous frames of the video

