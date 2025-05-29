ransacfitaffinefundmatrix - Fits affine fundamental matrix using RANSAC

```
Usage:   (F, inliers) = ransacfitaffinefundmatrix(x1, x2, t)

Arguments:
         x1  - 2xN or 3xN set of homogeneous points.  If the data is
               2xN it is assumed the homogeneous scale factor is 1.
         x2  - 2xN or 3xN set of homogeneous points such that x1<->x2.
         t   - The distance threshold between data point and the model
               used to decide whether a point is an inlier or not.
               Note that point coordinates are normalised to that their
               mean distance from the origin is sqrt(2).  The value of
               t should be set relative to this, say in the range
               0.001 - 0.01
```

Note that it is assumed that the matching of x1 and x2 are putative and it is expected that a percentage of matches will be wrong.

```
Returns:
         F       - The 3x3 fundamental matrix such that x2'Fx1 = 0.
         inliers - An array of indices of the elements of x1, x2 that were
                   the inliers for the best model.
```

See also: ransac(), fundmatrix(), affinefundmatrix()
