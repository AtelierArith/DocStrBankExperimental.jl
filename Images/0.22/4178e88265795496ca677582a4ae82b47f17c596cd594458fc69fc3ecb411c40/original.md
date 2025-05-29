```
sum = boxdiff(integral_image, ytop:ybot, xtop:xbot)
sum = boxdiff(integral_image, CartesianIndex(tl_y, tl_x), CartesianIndex(br_y, br_x))
sum = boxdiff(integral_image, tl_y, tl_x, br_y, br_x)
```

An integral image is a data structure which helps in efficient calculation of sum of pixels in a rectangular subset of an image. It stores at each pixel the sum of all pixels above it and to its left. The sum of a window in an image can be directly calculated using four array references of the integral image, irrespective of the size of the window, given the `yrange` and `xrange` of the window. Given an integral image -

```
    A - - - - - - B -
    - * * * * * * * -
    - * * * * * * * -
    - * * * * * * * -
    - * * * * * * * -
    - * * * * * * * -
    C * * * * * * D -
    - - - - - - - - -
```

The sum of pixels in the area denoted by * is given by S = D + A - B - C.
