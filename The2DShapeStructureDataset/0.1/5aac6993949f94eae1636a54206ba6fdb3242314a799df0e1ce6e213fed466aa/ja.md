```
shape_area(name)
```

[`shape_coords`](@ref)と同じ座標を返しますが、`Meshes.jl`の`PolyArea`として返します。

```julia
julia> shape_area("Bone-1")
PolyArea
  outer
  └─ Ring((x: 0.34174 m, y: 0.5 m), ..., (x: 0.34174 m, y: 0.5 m))
```
