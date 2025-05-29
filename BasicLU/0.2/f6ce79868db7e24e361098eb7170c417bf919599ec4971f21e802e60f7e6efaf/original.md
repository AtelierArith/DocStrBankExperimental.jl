```
factorize(F::LUFactor, B::SparseMatrixCSC{Float64, Int64}; check::Bool=true)
```

Factorize sparse matrix `B`, which must be square and have the dimension for which `F` was created.

The factorization method stops when all elements of the active submatrix are below the absolute pivot tolerance. In this case the `L` and `U` matrix are padded with columns of the identity matrix, yielding the factorization of a matrix `B*` which equals `B` except that the dependent columns are replaced by columns of the identity matrix. The number of actual pivot steps performed can be obtained with `getinfo(F, :nPivot)`.

When `check = true`, an error is thrown if the number of pivot steps is less than the dimension of `B`.
