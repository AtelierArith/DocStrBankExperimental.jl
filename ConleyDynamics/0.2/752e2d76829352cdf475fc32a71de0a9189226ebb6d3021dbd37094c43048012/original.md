```
cm_reduce!(matrix::SparseMatrix, psetvec::Vector{Int};
           [returnbasis::Bool],[returntm::Bool])
```

Compute the connection matrix.

Assumes that `matrix` is upper triangular and filtered according to `psetvec`. Modifies the argument `matrix`.

# Return values:

  * `cmatrix`: Connection matrix
  * `cmatrix_cols`: Columns of the connection matrix in the boundary
  * `basisvecs` (optional): If the argument `returnbasis=true` is given, this returns information about the computed basis. The k-th entry of `basisvecs` is a vector containing the columns making up the k-th basis vector, which corresponds to column `cmatrix_cols[k]`.
  * `tmatrix` (optional): If the argument `returntm=true` is given in addition to `returnbasis=true`, then instead of `basisvecs` the function returns the complete transformation matrix. In this case, `basicvecs` is not returned.
