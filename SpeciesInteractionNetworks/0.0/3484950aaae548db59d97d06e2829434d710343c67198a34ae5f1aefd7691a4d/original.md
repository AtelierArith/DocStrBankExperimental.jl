```
successors(N::SpeciesInteractionNetwork{Bipartite{T}, <:Interactions}, sp::T) where {T}
```

The successors of a species in a bipartite network is the list of all species it establishes a non-zero interaction with. For probabilistic networks, this includes all species with a non-zero probability of interaction.

If the species is at the bottom of the network, or if the specis has no successors, this method will retun an empty list of species, specifically `Set{T}()`.
