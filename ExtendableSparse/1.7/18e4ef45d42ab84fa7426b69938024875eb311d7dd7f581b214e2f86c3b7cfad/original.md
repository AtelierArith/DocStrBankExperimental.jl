```
 BlockPreconditioner(;partitioning, factorization=LUFactorization)
```

Create a block preconditioner from partition of unknowns given by `partitioning`, a vector of AbstractVectors describing the indices of the partitions of the matrix. For a matrix of size `n x n`, e.g. partitioning could be `[ 1:n÷2, (n÷2+1):n]` or [ 1:2:n, 2:2:n]. Factorization is a callable (Function or struct) which allows to create a factorization (with `ldiv!` methods) from a submatrix of A.
