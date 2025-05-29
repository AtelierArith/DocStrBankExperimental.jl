```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary}, ::Type{Connectance})
```

Permutations with a constraint by connectance will *randomly* (and with equal probability) perform a move that is constrained by degree, generality, or vulnerability.
