```
centrality(N::SpeciesInteractionNetwork{<:Unipartite, <:Union{Binary, Probabilistic}})
```

If no type is given as the first argument, the centrality function will use [`ClosenessCentrality`](@ref).
