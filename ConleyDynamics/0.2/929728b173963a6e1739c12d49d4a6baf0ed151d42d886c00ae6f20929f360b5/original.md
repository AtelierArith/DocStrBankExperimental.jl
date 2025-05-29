```
sparse_add_column!(matrix::SparseMatrix, ci1::Int, ci2::Int, cn, cd)
```

Replace `column[ci1]` by `column[ci1] + (cn/cd) * column[ci2]`.
