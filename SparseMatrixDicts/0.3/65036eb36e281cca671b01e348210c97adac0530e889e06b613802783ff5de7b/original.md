```
SparseMatrixDict{Tv,Ti<:Integer} <: AbstractSparseMatrix{Tv,Ti}
s = SparseMatrixDict{Tv,Ti}(m,n)
```

Matrix type for storing sparse matrices in the Dictionary format as Dict{Tuple{Ti,Ti},Tv}. The constructor accepts two arguments: the number of rows (m) and the number of columns (n).
