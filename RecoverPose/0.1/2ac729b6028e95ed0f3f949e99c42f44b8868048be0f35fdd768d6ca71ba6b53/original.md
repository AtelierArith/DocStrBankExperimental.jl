```julia
p3p(points, pdn_pixels::AbstractVector{SVector{3, T}}, K)
```

Recover pose using P3P algorithm.

# Arguments:

  * `points: Vector of 3D points in`(x, y, z)` format.
  * `pdn_pixels::AbstractVector{SVector{3, Float64}}`:   Corresponding projections of `points` onto image plane,   predivided by `K` intrinsics and normalized.   E.g.: `Ki = inv(K); p = Ki [x, y, 1]; p /= norm(p)`.
  * `K::SMatrix{3, 3, Float64}`: Camera intrinsics.

# Returns:

`Vector{SMatrix{3, 4, Float64}}` vector of up to 4 possible solutions. Each element is a projection matrix `P = K * [R|t]`. To get pure transformation matrix, multiply `P` by `inv(K)`.

# References:

```
Link: https://cmp.felk.cvut.cz/~pajdla/gvg/GVG-2016-Lecture.pdf
chapter: 7.3 Calibrated camera pose computation.
pages: 51-59
```
