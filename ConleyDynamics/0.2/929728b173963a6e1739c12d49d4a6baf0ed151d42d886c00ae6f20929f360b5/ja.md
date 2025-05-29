```
sparse_add_column!(matrix::SparseMatrix, ci1::Int, ci2::Int, cn, cd)
```

`column[ci1]`を`column[ci1] + (cn/cd) * column[ci2]`に置き換えます。
