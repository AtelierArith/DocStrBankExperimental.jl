```julia
p3p_ransac(points, pixels, K; threshold = 1.0, ransac_kwargs...)
```

Recover pose `K*[R|t]` using P3P Ransac algorithm.

# Arguments:

  * `points`: 3D points in `(x, y, z)`
  * `pixels`: Corresponding projections onto image plane in `(x, y)` format.   These values, **WILL** be predivided and normalized by the intrinsic matrix.   E.g.: `Ki = inv(K); p = Ki [x, y, 1]; p /= norm(p)`.
  * `K`: Camera intrinsics.
  * `threshold::Real`:   Maximum distance in pixels between projected point and its target pixel,   for the point to be considered inlier. Default value is `1.0`.
  * `ransac_kwargs...`: Keyword arguments passed to [`ransac`](@ref).

# Returns:

`Vector{SMatrix{3, 4, Float64}}` vector of up to 4 possible solutions. Each element is a projection matrix `P = K * [R|t]`. To get pure transformation matrix, multiply `P` by `inv(K)`.

# References:

```
Link: https://cmp.felk.cvut.cz/~pajdla/gvg/GVG-2016-Lecture.pdf
chapter: 7.3 Calibrated camera pose computation.
pages: 51-59
```
