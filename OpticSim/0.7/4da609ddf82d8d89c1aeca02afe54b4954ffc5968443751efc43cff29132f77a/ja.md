```
TriangleMesh{T} <: Surface{T}
```

メッシュを形成する[`Triangle`](@ref)の配列。視覚化の目的でのみ使用されます。

```julia
TriangleMesh(tris::Vector{Triangle{T}})
```
