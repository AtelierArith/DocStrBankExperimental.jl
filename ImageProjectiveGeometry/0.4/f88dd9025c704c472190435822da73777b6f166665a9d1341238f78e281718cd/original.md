ransacfitline - Fits line to 3D array of points using RANSAC

```
Usage  (V, L, inliers) = ransacfitline(XYZ, t, feedback)

This function uses the RANSAC algorithm to robustly fit a line to a
set of 3D data points or to a set of 2D homogeneous points with scale
value of 1

Arguments:
         XYZ - 3xNpts array of xyz coordinates to fit line to.
         t   - The distance threshold between data point and the line
               used to decide whether a point is an inlier or not.
    feedback - Optional boolean flag to turn on RANSAC feedback
               information.

Returns:.
          V - Line obtained by a simple fitting on the points that
              are considered inliers.  The line goes through the
              calculated mean of the inlier points, and is parallel to
              the principal eigenvector.  The line is scaled by the
              square root of the largest eigenvalue.
              This line is returned as a nx2 matrix.  The first column
              is the beginning point, the second column is the end point
              of the line.
          L - The two points in the data set that were found to
              define a line having the most number of inliers.
              The two columns of L defining the two points.
    inliers - The indices of the points that were considered
              inliers to the fitted line.
```

See also:  ransac(), fitplane(), ransacfitplane()
