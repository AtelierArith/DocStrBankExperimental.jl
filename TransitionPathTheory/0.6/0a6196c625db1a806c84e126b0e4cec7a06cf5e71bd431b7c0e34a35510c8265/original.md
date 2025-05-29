```
current2arrows(f, x, y; excluded = nothing)
```

Compute forward current vectors in a 2D physical space.

Return `(u, v)` where `u[i]` and `v[i]` are the `x` and `y` components of vector centered at `(x, y)` and pointing in the direction of the weighted average by `f[i,:]` of each other point.

### Arguments

  * `f`: `forward_current` computed from [`stationary_statistics`](@ref).
  * `x`: A `Vector` of points `[x1, x2, ...]`
  * `y`: A `Vector` of points `[y1, y2, ...]`

### Optional Arguments

  * `excluded`: If a `Vector{<:Integer}` is provided, rows and columns corresponding to them are excluded from `f`. When `excluded === nothing`, the last index of `f` is excluded automatically.
