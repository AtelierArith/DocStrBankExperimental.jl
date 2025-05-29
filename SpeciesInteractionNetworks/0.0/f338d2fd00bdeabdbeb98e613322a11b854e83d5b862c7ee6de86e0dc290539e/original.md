```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

Performs *one* swap of interactions in the network. If no `PermutationConstraint` is given as a second argument, the degree distribution of all species will be maintained.
