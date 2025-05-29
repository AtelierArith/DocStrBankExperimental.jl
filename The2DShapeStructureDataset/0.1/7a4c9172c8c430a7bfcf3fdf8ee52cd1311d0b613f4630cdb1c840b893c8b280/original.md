```
shape_ring(name)
```

Returns the same coordinates as [`shape_coords`](@ref) but as a `Ring` from `Meshes.jl`.

```julia
julia> shape_ring("Bone-1")
Ring
├─ Point(x: 0.34174 m, y: 0.5 m)
├─ Point(x: 0.3578 m, y: 0.52523 m)
├─ Point(x: 0.37615 m, y: 0.55046 m)
├─ Point(x: 0.3922 m, y: 0.57569 m)
├─ Point(x: 0.40826 m, y: 0.60092 m)
⋮
├─ Point(x: 0.28899 m, y: 0.41743 m)
├─ Point(x: 0.30505 m, y: 0.44266 m)
├─ Point(x: 0.32339 m, y: 0.46789 m)
├─ Point(x: 0.33945 m, y: 0.49312 m)
└─ Point(x: 0.34174 m, y: 0.5 m)
```
