```
allocate_matrix(::Type{Symmetric{Tv, SparseMatrixCSC{Tv, Ti}}}, sp::SparsityPattern)
```

Instantiate a sparse matrix of type `Symmetric{Tv, SparseMatrixCSC{Tv, Ti}}`, i.e. a `LinearAlgebra.Symmetric`-wrapped `SparseMatrixCSC`, from the sparsity pattern `sp`. The resulting matrix will only store entries above, and including, the diagonal.
