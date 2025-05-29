```julia
five_point(points1, points2, K1, K2; max_repr_error = 1.0)
```

Compute Essential matrix and recover pose from it for a given set of points. This function accepts five points, if you have more of them, consider using [`five_point_ransac`](@ref) version.

# Arguments:

  * `points1`:   Pixel coordinates of the matched points in `(x, y)` format   in the first image.
  * `points2`:   Pixel coordinates of the matched points in `(x, y)` format   in the second image.
  * `K1`: Intrinsic matrix for the first set of points.
  * `K2`: Intrinsic matrix for the second set of points.
  * `max_repr_error`: Maximum allowed reprojection error for a point to be   considered as inlier. Default is `1.0`.

# Returns:

`n_inliers, (E, P, inliers, repr_error)`:

  * number of inliers
  * tuple: essential matrix, pose matrix, boolean vector of inliers, error value.

!!! note
    Pose matrix transforms points from the first camera to the second camera.

