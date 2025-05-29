```
successors(N::SpeciesInteractionNetwork{Unipartite{T}, <:Interactions}, sp::T) where {T}
```

The successors of a species in a unipartite network is the list of all species it establishes a non-zero interaction with. For probabilistic networks, this includes all species with a non-zero probability of interaction.

If the specis has no successors, this method will retun an empty list of species, specifically `Set{T}()`.
