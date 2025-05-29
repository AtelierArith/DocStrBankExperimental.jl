```
SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40)
```

Create a solid cone with dimensions given by `length`, `width` and `height`, discretized into `n` triangles (must be even) and standard location and orientation.

# Arguments

  * `length = 1.0`: The length of the cone (distance between base and apex).
  * `width = 1.0`: The width of the base of the cone.
  * `height = 1.0`: The height of the base of the cone.
  * `n = 40`: The number of triangles to be used in the mesh.

# Examples

```jldoctest
julia> SolidCone(;length = 1.0, width = 1.0, height = 1.0, n = 40);
```
