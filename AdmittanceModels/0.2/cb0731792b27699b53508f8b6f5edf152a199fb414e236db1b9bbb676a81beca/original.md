```
sparse_nullbasis(mat::SparseMatrixCSC{<:Number, Int})
```

Let `mat` be a matrix with the following properties     - for any two rows of `mat` there is at most one column on which both rows are nonzero     - any column of `mat` has at most 2 nonzero values Produce a sparse matrix whose columns form a basis for the nullspace of `mat`.
