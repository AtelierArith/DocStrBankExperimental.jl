```
render(::Type{Bipartite}, N::SpeciesInteractionNetwork{<:Unipartite, <:Interactions})
```

Returns the bipartite projection of a unipartite network. By constructions, species cannot be shared between levels of bipartite network, so this operation may not always succeed. If it fails, it will throw a [`BipartiteProjectionFailed`](@ref) exception.
