```
integral_img = integral_image(img)
```

Returns the integral image of an image. The integral image is calculated by assigning to each pixel the sum of all pixels above it and to its left, i.e. the rectangle from (1, 1) to the pixel. An integral image is a data structure which helps in efficient calculation of sum of pixels in a rectangular subset of an image. See `boxdiff` for more information.
