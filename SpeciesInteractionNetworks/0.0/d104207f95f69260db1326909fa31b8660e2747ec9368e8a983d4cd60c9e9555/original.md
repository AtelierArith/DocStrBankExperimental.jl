```
distancetobase(N::SpeciesInteractionNetwork{<:Unipartite{T}, <:Interactions}, sp::T) where {T}
```

Default measure of [`distancetobase`](@ref) using the [`BellmanFord`](@ref) shortest paths and the maximum distance.
