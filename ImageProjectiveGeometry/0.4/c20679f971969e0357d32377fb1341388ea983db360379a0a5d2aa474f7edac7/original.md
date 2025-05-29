affinefundmatrix - Computes affine fundamental matrix from 4 or more points

Function computes the affine fundamental matrix from 4 or more matching points in a stereo pair of images.

```
Usage:   (F, e1, e2) = affinefundmatrix(x1, x2)
         (F, e1, e2) = affinefundmatrix(x)

Arguments:
         x1, x2 - Two sets of corresponding points defined as
                  2xN arrays of inhomogeneous image coordinates.

         x      - If a single argument is supplied it is assumed that it
                  is in the form x = [x1; x2]
Returns:
         F      - The 3x3 fundamental matrix such that x2'*F*x1 = 0.
         e1     - The epipole in image 1 such that F*e1 = 0
         e2     - The epipole in image 2 such that F'*e2 = 0
```

Usage with a single argument is intended for the use of this function with ransac()

The Gold Standard algorithm given by Hartley and Zisserman p351 (2nd Ed.) is used.

See also: fundmatrix()
