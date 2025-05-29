```
nullbasis(mat::AbstractMatrix{<:Number}; warn::Bool=true)
```

Return a `SparseMatrixCSC` whose columns form a basis for the null space of mat. If `mat` satisfies the conditions of `sparse_nullbasis`, a sparse matrix is returned. Otherwise a warning is issued and the `LinearAlgebra.nullspace` function is used.
