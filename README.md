# Shadow-Removal
| **Coded by** |  |
| --- | --- |
| Pratham Arora | B.Tech, ECE, IITG |
| Vusuvandla Khagesh Kumar | B.Tech, ECE, IITG |

 **Introduction:** 

Shadows in an image can be defined as parts of the scene that are not directly illuminated by the light source due to an obstructing object or objects. Shadows and shadings in images lead to undesirable problems in image analysis. That is why, our project focuses on the issue of **shadow detection and removal**.

 **Methodology:** 

- The foremost step in the process of shadow removal is the shadow detection.
- For shadow detection, we convert the BGR input image to YCbCr color space image. The we calculate the mean of the pixel values along the Y-plane. Further, we calculated the standard deviation along the Y-plane.
- We set (y\_mean-(y\_std/3)) as the threshold. Perform a sliding window over all the pixels. If the intensity value of pixel in YCbCr image is less than the threshold, we classify it as the shadowed region, else we classify it as the non-shadowed region.
- In a binary mask we give pixel value (1,1,1) to shadowed region and (0,0,0) to non-shadowed region and keep the first value of each pixel, thus, we obtain a 2 dimensional matrix for binary mask with value 1 for shadowed region and value 0 for non-shadowed region.
- From the original input image we calculate average pixel value of the shadowed image in numpy array one and average pixel value of non-shadowed image in the numpy array zero and convert the data type in both the numpy arrays to int64.
- Calculate the difference of average pixel values of non shadowed and shadowed regions, and add this difference as the bias to shadowed region. For this, we again perform the sliding window over all the pixels of binary mask and alter pixels of shadowed regions in the original image to create a shadow-free image.

**Results:**

| _Input Image_ | _Shadow free image_ |
| --- | --- |
| ![shadowtest1](https://user-images.githubusercontent.com/45618170/122661758-7a83c180-d1ab-11eb-883d-51114f89b93f.png) | ![shadowtest1_result](https://user-images.githubusercontent.com/45618170/122661778-a43ce880-d1ab-11eb-989f-052d4f4e7d40.jpg) |
| ![shadowtest2](https://user-images.githubusercontent.com/45618170/122661760-8079a280-d1ab-11eb-91b4-88eaa812cca8.png) | ![shadowtest2_result](https://user-images.githubusercontent.com/45618170/122661774-a1da8e80-d1ab-11eb-9456-31a9aaa66ad0.jpg) |
| ![shadowtest3](https://user-images.githubusercontent.com/45618170/122661762-87081a00-d1ab-11eb-825b-64021eff9f49.png) | ![shadowtest3_result](https://user-images.githubusercontent.com/45618170/122661775-a30bbb80-d1ab-11eb-8f87-9638c1fd2452.jpg) |
| ![shadowtest4](https://user-images.githubusercontent.com/45618170/122661763-8b343780-d1ab-11eb-9d56-f7961dea1420.png) | ![shadowtest4_result](https://user-images.githubusercontent.com/45618170/122661776-a3a45200-d1ab-11eb-94cc-2da9a33e4698.jpg) |
