```
h_dim(objects::Vector{Vector{Tuple{T, S}}}; offset = zero(S)) where {T, S}
```

オブジェクトのコレクションの水平方向の次元を計算します。

# 引数

  * `objects::Vector{Vector{Tuple{T, S}}}`: 各内部ベクターが型 `(T, S)` のタプルを含むベクターのベクター。
  * `offset`: 型 `S` のオプションのオフセット値。デフォルトは `zero(S)`。

# 戻り値

  * `HDimensions` オブジェクトが含まれます：

      * `x_dims`: 計算された x 次元。
      * `y_dims`: 調整された y 次元。
      * `labels`: 次元ラベル。
      * `minor_lines`: 次元のためのマイナーライン。
      * `major_lines`: 次元のためのメジャーライン。
      * `offset`: 参照オブジェクトからのオフセット。
