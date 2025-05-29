```
render(::Type{Unipartite}, N::SpeciesInteractionNetwork{<:Bipartite, <:Interactions})
```

Returns the unipartite projection of a bipartite network. By constructions, species cannot be shared between levels of bipartite network, so this operation will always succeed.
