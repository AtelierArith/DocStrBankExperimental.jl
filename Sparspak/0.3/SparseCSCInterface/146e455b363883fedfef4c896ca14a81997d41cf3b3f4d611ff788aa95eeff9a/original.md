```
sparspaklu!(lu::SparseSolver, m::SparseMatrixCSC; allow_pattern_change=true) -> lu::SparseSolver
```

Calculate LU factorization of a sparse matrix `m`, reusing ordering and symbolic factorization `lu`, if that was previously calculated.

If `allow_pattern_change = true` (the default) the sparse matrix `m` may have a nonzero pattern different to that of the matrix used to create the LU factorization `lu`, in which case the ordering and symbolic factorization are updated.

If `allow_pattern_change = false` an error is thrown if the nonzero pattern of `m` is different to that  of the matrix used to create the LU factorization `lu`.

If `lu` has not been factorized (ie it has just been created with option `factorize = false`) then  `lu` is always updated from `m` and `allow_pattern_change` is ignored.
