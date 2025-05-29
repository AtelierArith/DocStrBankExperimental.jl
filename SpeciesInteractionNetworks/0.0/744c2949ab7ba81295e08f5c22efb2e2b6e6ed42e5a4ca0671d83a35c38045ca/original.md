```
simplify(N::SpeciesInteractionNetwork{<:Bipartite, <:Interactions})
```

Returns a *copy* of a network containing only the species with interactions. Internally, this calls [`isdisconnected`](@ref).
