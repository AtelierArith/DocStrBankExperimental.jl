```
CartesianMesh([T,] h, (xmin, xmax), (ymin, ymax)...)
```

Construct `CartesianMesh` with the spacing `h`.

# Examples

```jldoctest
julia> CartesianMesh(1.0, (0,3), (1,4))
4×4 CartesianMesh{2, Float64, Vector{Float64}}:
 [0.0, 1.0]  [0.0, 2.0]  [0.0, 3.0]  [0.0, 4.0]
 [1.0, 1.0]  [1.0, 2.0]  [1.0, 3.0]  [1.0, 4.0]
 [2.0, 1.0]  [2.0, 2.0]  [2.0, 3.0]  [2.0, 4.0]
 [3.0, 1.0]  [3.0, 2.0]  [3.0, 3.0]  [3.0, 4.0]
```
