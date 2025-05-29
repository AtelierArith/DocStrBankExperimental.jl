```
v_dim(xs::Vector{Vector{T}}, ys::Vector{Vector{S}}; offset = zero(T)) where {T, S}
```

与えられた x および y 座標のセットに対して垂直次元を計算します。

# 引数

  * `xs::Vector{Vector{T}}`: x 座標を含むベクトルのベクトル。
  * `ys::Vector{Vector{S}}`: y 座標を含むベクトルのベクトル。
  * `offset`: デフォルト値 `zero(S)` のオプションのパラメータで、x 次元を調整するために使用されます。

# 戻り値

  * `VDimensions` オブジェクトには以下が含まれます：

      * `x_dims`: オフセットによって調整された x 次元。
      * `y_dims`: y 次元。
      * `labels`: 次元ラベル。
      * `minor_lines`: 次元のためのマイナーライン。
      * `major_lines`: 次元のためのメジャーライン。
      * `offset`: 参照オブジェクトからのオフセット。
