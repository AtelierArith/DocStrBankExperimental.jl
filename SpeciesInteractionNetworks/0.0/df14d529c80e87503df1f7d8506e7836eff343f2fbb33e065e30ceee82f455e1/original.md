```
distancetobase(N::SpeciesInteractionNetwork{<:Unipartite{T}, <:Interactions}, sp::T, f) where {T}
```

Default measure of [`distancetobase`](@ref) using the [`BellmanFord`](@ref) shortest paths and the distance returned by `f`.
