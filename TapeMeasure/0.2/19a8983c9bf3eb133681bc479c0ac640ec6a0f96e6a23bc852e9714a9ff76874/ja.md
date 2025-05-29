```
mutable struct Labels{T, S}
```

次元オブジェクトのラベル付き情報を保持する構造体です。

# フィールド

  * `xs::Vector{T}`: 型 `T` の x 座標のベクトル。
  * `ys::Vector{S}`: 型 `S` の y 座標のベクトル。
  * `lbls::Vector{String}`: データポイントに対応するラベルのベクトル。
