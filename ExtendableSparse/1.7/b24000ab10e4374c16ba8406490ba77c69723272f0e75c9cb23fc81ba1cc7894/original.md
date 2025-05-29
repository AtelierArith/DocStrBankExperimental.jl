```
 BlockPreconBuilder(;precs=UMFPACKPreconBuilder(),  
                     partitioning = A -> [1:size(A,1)]
```

Return callable object constructing a left block Jacobi preconditioner  from partition of unknowns.

  * `partitioning(A)`  shall return a vector of AbstractVectors describing the indices of the partitions of the matrix.  For a matrix of size `n x n`, e.g. partitioning could be `[ 1:n÷2, (n÷2+1):n]` or [ 1:2:n, 2:2:n].
  * `precs(A,p)` shall return a left precondioner for a matrix block.
