```
complexstoichmat(network::ReactionSystem; sparse=false)
```

Given a [`ReactionSystem`](@ref) and vector of reaction complexes, return a matrix with positive entries of size number of species by number of complexes, where the non-zero positive entries in the kth column denote stoichiometric coefficients of the species participating in the kth reaction complex.

Notes:

  * Set sparse=true for a sparse matrix representation
