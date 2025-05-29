```julia
five_point_ransac(
    points1, points2, K1, K2; max_repr_error = 1.0, ransac_kwargs...)
```

Compute Essential matrix and recover pose from it using RANSAC scheme.

# Arguments:

  * `points1`:   Pixel coordinates of the matched points in `(x, y)` format   in the first image.
  * `points2`:   Pixel coordinates of the matched points in `(x, y)` format   in the second image.
  * `K1`: Intrinsic matrix for the first set of points.
  * `K2`: Intrinsic matrix for the second set of points.
  * `max_repr_error`: Maximum allowed reprojection error for a point to be   considered as inlier. Default is `1.0`.
  * `ransac_kwargs...`: Keyword arguments passed to [`ransac`](@ref).

# Returns:

`n_inliers, (E, P, inliers, repr_error)`:

  * number of inliers
  * tuple: essential matrix, pose matrix, boolean vector of inliers, error value.

!!! note
    Pose matrix transforms points from the first camera to the second camera.

