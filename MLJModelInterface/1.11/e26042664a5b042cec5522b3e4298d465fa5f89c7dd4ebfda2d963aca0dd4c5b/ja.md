```
matrix(X; transpose=false)
```

もし `X isa AbstractMatrix` の場合、`X` を返すか、`transpose=true` の場合は `permutedims(X)` を返します。それ以外の場合、`X` が Tables.jl 互換のテーブルソースであれば、`X` を `Matrix` に変換します。
