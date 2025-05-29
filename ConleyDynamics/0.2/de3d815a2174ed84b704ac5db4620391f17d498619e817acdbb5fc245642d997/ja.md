```
sparse_add_row!(matrix::SparseMatrix, ri1::Int, ri2::Int, cn, cd)
```

`row[ri1]`を`row[ri1] + (cn/cd) * row[ri2]`に置き換えます。
