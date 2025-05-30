```
Chol(X::AbstractMatrix{T}) where {T<:Base.IEEEFloat}
```

`n`次元のランダム変数のサンプルである`q × n`行列からCholesky変換器を構築します。

結果の共分散行列が正定値であるためには、`q`は`n`以上でなければならず、分散がゼロであってはなりません。
