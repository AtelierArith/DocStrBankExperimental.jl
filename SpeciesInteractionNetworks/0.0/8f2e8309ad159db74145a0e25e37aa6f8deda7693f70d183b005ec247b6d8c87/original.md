```
predecessors(N::SpeciesInteractionNetwork{Bipartite{T}, <:Interactions}, sp::T) where {T}
```

The predecessors of a species in a bipartite network is the list of all species it receives a non-zero interaction from. For probabilistic networks, this includes all species with a non-zero probability of interaction.

If the species is at the top of the network, or if the specis has no predecessors, this method will retun an empty list of species, specifically `Set{T}()`.
