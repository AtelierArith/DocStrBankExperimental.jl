```
sparse_add_row!(matrix::SparseMatrix{Int}, ri1::Int, ri2::Int,
                cn::Int, cd::Int)
```

Replace `row[ri1]` by `row[ri1] + (cn/cd) * row[ri2]`.

The computation is performed mod p, where the characteristic is taken from `matrix.char`. An error is thrown if `matrix.char==0`.
