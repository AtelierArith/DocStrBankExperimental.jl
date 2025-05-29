```julia
struct ConvexHull{O<:PlanarConvexHulls.VertexOrder, T, P<:StaticArrays.StaticArray{Tuple{2}, T, 1}, V<:AbstractArray{P<:StaticArrays.StaticArray{Tuple{2}, T, 1}, 1}}
```

2Dポイントの集合の凸包を、その極端な点（頂点）によって表し、最初の型パラメータによって与えられた[`VertexOrder`](@ref)に従って保存されます。
