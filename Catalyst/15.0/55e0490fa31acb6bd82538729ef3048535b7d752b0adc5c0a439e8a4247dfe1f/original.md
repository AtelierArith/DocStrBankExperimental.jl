```
prodstoichmat(rn; sparse=false)
```

Returns the product stoichiometry matrix, $P$, with $P_{i j}$ the stoichiometric coefficient of the ith product within the jth reaction.

Note:

  * Set sparse=true for a sparse matrix representation
  * Note that constant species are not treated as products, but just components that modify the associated rate law.
