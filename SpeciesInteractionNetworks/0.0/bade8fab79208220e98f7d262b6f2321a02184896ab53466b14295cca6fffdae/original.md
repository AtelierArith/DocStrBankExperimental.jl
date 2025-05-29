```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary}, ::Type{Degree})
```

Permutations with a constraint by degree work by picking two interacting species pairs, (r1, s1) and (r2, s2), and trying to replace them by (r1, s2) and (r2, s1).
