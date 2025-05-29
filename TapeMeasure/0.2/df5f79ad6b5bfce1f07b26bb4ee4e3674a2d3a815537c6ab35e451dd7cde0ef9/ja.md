```
h_dim(xs::Vector{Vector{T}}, ys::Vector{Vector{S}}; offset = zero(S)) where {T, S}
```

この関数は、入力ベクトル `xs` と `ys` に基づいて水平方向の次元を計算します。

# 引数

  * `xs::Vector{Vector{T}}`: x座標を含むベクトルのベクトル。
  * `ys::Vector{Vector{S}}`: y座標を含むベクトルのベクトル。
  * `offset`: y次元を調整するために使用されるデフォルト値 `zero(S)` のオプションパラメータ。

# 戻り値

  * `HDimensions` オブジェクトには以下が含まれます：

      * `x_dims`: 計算された x 次元。
      * `y_dims`: 調整された y 次元。
      * `labels`: 次元ラベル。
      * `minor_lines`: 次元のためのマイナーライン。
      * `major_lines`: 次元のためのメジャーライン。
      * `offset`: 参照オブジェクトからのオフセット。
