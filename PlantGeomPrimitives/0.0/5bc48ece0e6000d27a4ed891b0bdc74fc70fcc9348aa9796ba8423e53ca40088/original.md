```
Ellipse(;length = 1.0, width = 1.0, n = 20)
```

Create a triangular mesh approximating an ellipse with dimensions given by `length` and `width`, discretized into `n` triangles (must be even) and standard location and orientation.

# Arguments

  * `length = 1.0`: The length of the ellipse.
  * `width = 1.0`: The width of the ellipse.
  * `n = 20`: The number of triangles to be used in the mesh.

# Examples

```jldoctest
julia> Ellipse(;length = 1.0, width = 1.0, n = 20);
```
