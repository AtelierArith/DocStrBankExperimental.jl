```
distancetobase(N::SpeciesInteractionNetwork{<:Unipartite{T}, <:Interactions}, sp::T) where {T}
```

[`distancetobase`](@ref) のデフォルト測定は、[`BellmanFord`](@ref) 最短経路と最大距離を使用します。
