```
sparse_add_row!(matrix::SparseMatrix, ri1::Int, ri2::Int, cn, cd)
```

Replace `row[ri1]` by `row[ri1] + (cn/cd) * row[ri2]`.
