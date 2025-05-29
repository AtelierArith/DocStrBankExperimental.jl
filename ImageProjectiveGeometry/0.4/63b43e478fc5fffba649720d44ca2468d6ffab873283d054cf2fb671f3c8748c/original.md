ransacfitplane - Fits plane to 3D array of points using RANSAC

```
Usage  (B, P, inliers) = ransacfitplane(XYZ, t, feedback)

This function uses the RANSAC algorithm to robustly fit a plane
to a set of 3D data points.

Arguments:
         XYZ - 3xNpts array of xyz coordinates to fit plane to.
         t   - The distance threshold between data point and the plane
               used to decide whether a point is an inlier or not.
         feedback - Optional flag 0 or 1 to turn on RANSAC feedback
                    information.

Returns:
          B - 4x1 array of plane coefficients in the form
              b[1]*X + b[2]*Y +b[3]*Z + b[4] = 0
              The magnitude of B is 1.
              This plane is obtained by a least squares fit to all the
              points that were considered to be inliers, hence this
              plane will be slightly different to that defined by P below.
          P - The three points in the data set that were found to
              define a plane having the most number of inliers.
              The three columns of P defining the three points
    inliers - The indices of the points that were considered
              inliers to the fitted plane.
```

See also:  ransac(), fitplane()
