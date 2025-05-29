```
neighboringnodes(x::Vec, r::Real, mesh::CartesianMesh)
```

Return `CartesianIndices` for neighboring nodes around `x`. `r` denotes the range for searching area. In 1D, for example, the range `a` becomes `x-r*h ≤ a < x+r*h` where `h` is `spacing(mesh)`.

# Examples

```jldoctest
julia> mesh = CartesianMesh(1, (0,5))
6-element CartesianMesh{1, Float64, Vector{Float64}}:
 [0.0]
 [1.0]
 [2.0]
 [3.0]
 [4.0]
 [5.0]

julia> neighboringnodes(Vec(1.5), 1, mesh)
CartesianIndices((2:3,))

julia> neighboringnodes(Vec(1.5), 3, mesh)
CartesianIndices((1:5,))
```
