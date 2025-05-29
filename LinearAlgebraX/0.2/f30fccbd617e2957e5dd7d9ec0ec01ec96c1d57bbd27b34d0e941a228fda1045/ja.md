```
cofactor_det(A::AbstractMatrix{T}) where {T}
```

`cofactor(A::AbstractMatrix{T})` は、余因子展開を使用して `A` の行列式を計算します（これは遅くなる可能性があります）。このメソッドの戻り値の型は `T` の数です。`A` のエントリは多項式であり、これはJuliaの `det` では機能しません。
