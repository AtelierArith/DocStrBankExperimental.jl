```
SolidCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 80)
```

Create a solid cylinder with dimensions given by `length`, `width` and `height`, discretized into `n` triangles (must be even) and standard location and orientation.

# Arguments

  * `length = 1.0`: The length of the cylinder (distance between bases).
  * `width = 1.0`: The width of the base of the cylinder.
  * `height = 1.0`: The height of the base of the cylinder.
  * `n = 80`: The number of triangles to discretize the cylinder into.

# Examples

```jldoctest
julia> SolidCylinder(;length = 1.0, width = 1.0, height = 1.0, n = 80);
```
