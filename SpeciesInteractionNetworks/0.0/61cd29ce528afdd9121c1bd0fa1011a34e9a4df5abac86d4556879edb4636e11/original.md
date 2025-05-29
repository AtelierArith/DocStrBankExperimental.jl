```
findmotif(M::SpeciesInteractionNetwork{<:Unipartite, <:Binary}, N::SpeciesInteractionNetwork{<:Unipartite, <:Binary})
```

Search for all groups of species in `N` that match the motif `M` – note that the motif to search is the *first* argument.
