```
pos_center(a::Array{T}) where T <: AbstractParticle
pos_center(a::StructArray)
```

等しい重みで平均位置を計算します。これは、遠くの粒子からの影響を避けるためにシンボルの中央値を計算する `middle(a, :Pos)` とは異なります。

`center`、`pos_center`、`mass_center`、および `median` の間には違いがあります：

  * `center`: 粒子のボックス中心
  * `pos_center`: 粒子の平均位置
  * `mass_center`: 粒子の質量加重平均位置
  * `median`: 粒子の位置の中央値
