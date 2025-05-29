```
sparse_add_column!(matrix::SparseMatrix{Int}, ci1::Int, ci2::Int,
                   cn::Int, cd::Int)
```

Replace `column[ci1]` by `column[ci1] + (cn/cd) * column[ci2]`.

The computation is performed mod p, where the characteristic is taken from `matrix.char`. An error is thrown if `matrix.char==0`.
