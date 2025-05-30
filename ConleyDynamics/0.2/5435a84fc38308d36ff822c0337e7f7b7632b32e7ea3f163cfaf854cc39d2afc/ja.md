```
sparse_add_row!(matrix::SparseMatrix{Int}, ri1::Int, ri2::Int,
                cn::Int, cd::Int)
```

`row[ri1]`を`row[ri1] + (cn/cd) * row[ri2]`に置き換えます。

計算はpで行われ、特性は`matrix.char`から取られます。`matrix.char==0`の場合はエラーが発生します。
