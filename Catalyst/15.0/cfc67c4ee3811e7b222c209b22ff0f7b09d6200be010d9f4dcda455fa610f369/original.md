```
netstoichmat(rn, sparse=false)
```

Returns the net stoichiometry matrix, $N$, with $N_{i j}$ the net stoichiometric coefficient of the ith species within the jth reaction.

Notes:

  * Set sparse=true for a sparse matrix representation
  * Caches the matrix internally within `rn` so subsequent calls are fast.
  * Note that constant species are not treated as reactants, but just components that modify the associated rate law. As such they do not contribute to the net stoichiometry matrix.
