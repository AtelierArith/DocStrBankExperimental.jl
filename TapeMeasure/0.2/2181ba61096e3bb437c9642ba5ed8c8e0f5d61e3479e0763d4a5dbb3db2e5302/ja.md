```
dim_left(xs::Vector{T}, ys::Vector{S}; offset::S=0) -> Union{RightDimensions, LeftDimensions}
dim_left(object::Vector{Tuple{T, S}}; offset=zero(T)) where {T, S}
```

与えられたオブジェクトの x および y 座標のセットの左の次元を計算します。

# 引数

  * `xs::Vector{T}`: x 座標のベクトル。
  * `ys::Vector{S}`: y 座標のベクトル。
  * `offset`: 型 `S` のオプションのオフセット値。デフォルトはゼロです。

# 戻り値

  * `VDimensions` オブジェクトには以下が含まれます：

      * `x_dims`: オフセットによって調整された x 次元。
      * `y_dims`: y 次元。
      * `labels`: 次元ラベル。
      * `minor_lines`: 次元のマイナーライン。
      * `major_lines`: 次元のメジャーライン。
      * `offset`: 参照オブジェクトからのオフセット

オフセットが提供されていない場合、x 座標の範囲の 10% に設定されます。関数は次に、x および y 次元、メジャーおよびマイナーライン、ラベルを計算し、オフセット値に基づいて適切な次元オブジェクトを返します。
