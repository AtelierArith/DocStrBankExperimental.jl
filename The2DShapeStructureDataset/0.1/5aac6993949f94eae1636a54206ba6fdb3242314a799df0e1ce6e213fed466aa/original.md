```
shape_area(name)
```

Returns the same coordinates as [`shape_coords`](@ref) but as a `PolyArea` from `Meshes.jl`.

```julia
julia> shape_area("Bone-1")
PolyArea
  outer
  └─ Ring((x: 0.34174 m, y: 0.5 m), ..., (x: 0.34174 m, y: 0.5 m))
```
