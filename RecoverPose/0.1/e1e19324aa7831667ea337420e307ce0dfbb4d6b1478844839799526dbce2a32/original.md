```julia
essential_ransac(pd1, pd2, focal_sum; threshold = 1.0, ransac_kwargs...)
```

Compute Essential matrix using the RANASC scheme.

# Arguments:

  * `pd1`:   Pixel coordinates **predivided** by `K^-1` of the matched points   in `(x, y)` format in the first image.
  * `pd2`:   Pixel coordinates **predivided** by `K^-1` of the matched points   in `(x, y)` format in the second image.
  * `focal_sum`: `fx + fy`.
  * `threshold`: Maximum error for the epipolar constraint. Default is `1.0`.
  * `ransac_kwargs...`: Keyword arguments passed to [`ransac`](@ref).

# Returns:

`n_inliers, (E, inliers, repr_error)`:

  * number of inliers
  * tuple: essential matrix, boolean vector of inliers, error value.
