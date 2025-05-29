```
distancetobase(N::SpeciesInteractionNetwork{<:Unipartite{T}, <:Interactions}, sp::T, f) where {T}
```

[`distancetobase`](@ref) のデフォルト測定は、[`BellmanFord`](@ref) 最短経路と `f` によって返される距離を使用します。
