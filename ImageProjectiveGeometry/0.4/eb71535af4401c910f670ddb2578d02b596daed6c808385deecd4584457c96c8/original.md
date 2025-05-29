homography1d - Computes 1D homography

```
Usage:   H = homography1d(x1, x2)

Arguments:
         x1  - 2xN set of homogeneous points
         x2  - 2xN set of homogeneous points such that x1<->x2
Returns:
          H - the 2x2 homography such that x2 = H*x1
```

This code is modelled after the normalised direct linear transformation algorithm for the 2D homography given by Hartley and Zisserman p92.
