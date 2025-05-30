```
sparse_add_column!(matrix::SparseMatrix{Int}, ci1::Int, ci2::Int,
                   cn::Int, cd::Int)
```

`column[ci1]`を`column[ci1] + (cn/cd) * column[ci2]`に置き換えます。

計算はpで行われ、特性は`matrix.char`から取得されます。`matrix.char==0`の場合はエラーが発生します。
