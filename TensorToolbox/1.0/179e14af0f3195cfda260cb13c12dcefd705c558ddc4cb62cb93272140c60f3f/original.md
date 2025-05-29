```
normalize!(X[,n,normtype,factor])
```

Normalize columns of factor matrices of a ktensor. Rewrite ktensor. Also ensures that lambda is positive.

## Arguments:

  * `n`: Absorbe the excess weight into nth factor matrix.  If n=0, equally divide the weights across the factor matrices and set lambda to vector of ones.  If n="sort", sort the components by lambda value, from greatest to least.
  * `normtype`: Default: 2.
  * `factor`: Just normalize specified factor.
