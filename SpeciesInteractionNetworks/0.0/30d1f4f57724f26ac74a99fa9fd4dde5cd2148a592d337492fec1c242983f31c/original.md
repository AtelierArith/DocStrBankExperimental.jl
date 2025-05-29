```
shortestpath(N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Interactions}, sp::T)
```

Defaults to [`BellmanFord`](@ref) for the shortest path algorithm. See also [`Dijkstra`](@ref).

Note that in order to work with [`pathbetween`](@ref), any overload of [`shortestpath`](@ref) *must* accept an `include_paths` keyword argument, that when `true` returns a *second* dictionary giving the predecessors of each reached node.
