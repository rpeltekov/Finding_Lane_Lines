# **Finding Lane Lines on the Road** 
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. The Pipeline:

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied a gaussian blur with kernel size 5 onto it. Afterwards, I run the image through the canny algorithm to detect edges, and then select a region of interest with a trapezoid. The trapezoid contains largely the triangle area formed by the center of the image and the two bottom corners. Then, that resulting image is run through the hough transform algorithm to determing equations of lines that fit the edges. I then use the draw lines function to use these equations and draw lines on the original image to highlight the lanes. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by getting average slope of the each line output from the hough transform. I then throw out any erroneous slope that is known to not be an edge of a lane line. Then, I split average out the right and left lane slopes by splitting by the sign of the slope. Afterwards, using the average centers of the right and left lanes, I determing the average y-intercept to complete the equations of the two average lane lines. I then form the lines and draw them onto the image. 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Potential shortcomings with current pipeline


One potential shortcoming would be what would happen when there are changes in the road material and thus changes in the way the road appears on camera. This could make it so that there is not as much difference in brightness between the lane lines and the ground, making identification not as robust. 

Another shortcoming could be this software is designed to work for highway lane detection. It is not tested on other road types. 


### 3. Possible improvements to the pipeline

A possible improvement would be to do more trial and error to identify better parameters for the pipeline algorithms.

Another potential improvement could be to not rely on just picture feed from cameras to determine lane lines, but also other types of sensors.
