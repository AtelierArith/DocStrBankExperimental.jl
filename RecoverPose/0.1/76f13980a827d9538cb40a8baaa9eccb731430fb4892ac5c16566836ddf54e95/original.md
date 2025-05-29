```julia
p3p_ransac(points, pixels, pdn_pixels, K; threshold = 1.0, ransac_kwargs...)
```

Recover pose `K*[R|t]` using P3P Ransac algorithm.

# Arguments:

  * `points`: 3D points in `(x, y, z)`
  * `pixels`: Corresponding projections onto image plane in `(x, y)` format.
  * `pdn_pixels`: Corresponding projections onto image plane,   predivided by `K` intrinsics and normalized.   E.g.: `Ki = inv(K); p = Ki [x, y, 1]; p /= norm(p)`.
  * `K`: Camera intrinsics.
  * `threshold`: Maximum distance in pixels between projected point   and its target pixel, for the point to be considered inlier.   Default value is `1.0`.
  * `ransac_kwargs...`: Keyword arguments passed to [`ransac`](@ref).

# Returns:

`n_inliers, (projection, inliers, error)`.

  * `n_inliers`: Number of inliers for the `projection`.
  * `projection`: `K * P` projection matrix that projects `points`   onto image plane.
  * `inliers`: Boolean vector indicating which point is inlier.
  * `error`: Average reprojection error for the `pose`.

# References:

```
Link: https://cmp.felk.cvut.cz/~pajdla/gvg/GVG-2016-Lecture.pdf
chapter: 7.3 Calibrated camera pose computation.
pages: 51-59
```
