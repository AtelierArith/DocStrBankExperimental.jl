```julia
p3p_select_model(models, points, pixels; threshold = 1.0)
```

Select best pose from `models`.

# Arguments:

  * `models`: Projection matrices from which to select best one.
  * `points`: 3D points in `(x, y, z)`
  * `pixels`: Corresponding projections onto image plane in `(x, y)` format.
  * `threshold`: Maximum distance in pixels between projected point   and its target pixel, for the point to be considered inlier.   Default value is `1.0`.

# Returns:

`n_inliers, (projection, inliers, error)`.

  * `n_inliers`: Number of inliers for the `projection`.
  * `projection`: `K * P` projection matrix that projects `points`   onto image plane.
  * `inliers`: Boolean vector indicating which point is inlier.
  * `error`: Average reprojection error for the `pose`.
