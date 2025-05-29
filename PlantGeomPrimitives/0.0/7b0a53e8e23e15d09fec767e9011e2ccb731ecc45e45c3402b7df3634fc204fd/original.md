```
SolidFrustum(;length = 1.0, width = 1.0, height = 1.0, ratio = 1.0, n = 40)
```

Create a solid frustum with dimensions given by `length`, `width` and `height`, discretized into `n` triangles and standard location and orientation.

# Arguments

  * `length = 1.0`: The length of the frustum (distance between bases).
  * `width = 1.0`: The width of the base of the frustum.
  * `height = 1.0`: The height of the base of the frustum.
  * `ratio = 1.0`: The ratio between the top and bottom base radii.
  * `n = 40`: The number of triangles to discretize the frustum into.

# Examples

```jldoctest
julia> SolidFrustum(;length = 1.0, width = 1.0, height = 1.0, n = 40, ratio = 0.5);
```
