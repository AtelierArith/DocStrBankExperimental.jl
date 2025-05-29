fundmatrix - Computes fundamental matrix from 8 or more points

Function computes the fundamental matrix from 8 or more matching points in a stereo pair of images.  The normalised 8 point algorithm given by Hartley and Zisserman p265 is used.  To achieve accurate results it is recommended that 12 or more points are used

```
Usage:   (F, e1, e2) = fundmatrix(x1, x2)
         (F, e1, e2) = fundmatrix(x)

Arguments:
         x1, x2 - Two sets of corresponding 3xN set of homogeneous
         points.

         x      - If a single argument is supplied it is assumed that it
                  is in the form x = [x1; x2]
Returns:
         F      - The 3x3 fundamental matrix such that x2'*F*x1 = 0.
         e1     - The epipole in image 1 such that F*e1 = 0
         e2     - The epipole in image 2 such that F'*e2 = 0
```

Usage with a single argument is intended for the use of this function with ransac()

See also: affinefundmatrix()
