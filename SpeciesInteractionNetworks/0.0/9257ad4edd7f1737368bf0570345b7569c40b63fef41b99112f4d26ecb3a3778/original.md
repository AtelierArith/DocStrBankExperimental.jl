```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary}, ::Type{Generality})
```

Permutations with a constraint by degree work by picking one interacting species pair, (r1, s1), and a new stem species s3, trying to replace them by (r1, s3). This function only applies if the result of this permutations does not remove the last incoming link from s1.
