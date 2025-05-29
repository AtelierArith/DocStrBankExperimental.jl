homography2d - Computes 2D homography

```
Usage 1:   H = homography2d(x1, x2)

Arguments:
         x1  - 3xN set of homogeneous points
         x2  - 3xN set of homogeneous points such that x1<->x2


Usage 2:    H = homography2d(x)
Argument:
          x  - If a single argument is supplied it is assumed that it
               is in the form x = [x1; x2]

Returns:
         H - the 3x3 homography such that x2 = H*x1
```

Usage 2 is intended for use with ransac()

This code follows the normalised direct linear transformation algorithm given by Hartley and Zisserman "Multiple View Geometry in Computer Vision" p92.
