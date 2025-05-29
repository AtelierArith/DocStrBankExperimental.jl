```
substoichmat(rn; sparse=false)
```

Returns the substrate stoichiometry matrix, $S$, with $S_{i j}$ the stoichiometric coefficient of the ith substrate within the jth reaction.

Note:

  * Set sparse=true for a sparse matrix representation
  * Note that constant species are not considered substrates, but just components that modify the associated rate law.
