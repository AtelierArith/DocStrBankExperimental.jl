```
make_posdef!(A::Matrix{T}) where {T}
```

行列の固有値を調整することで、行列が正定値であることを保証します。

# 引数

  * `A::Matrix{T}`: 入力行列。

# 戻り値

  * `A` から導出された正定値行列。
