```
mass_center(a::Array{T}) where T <: AbstractParticle
mass_center(a::StructArray)
```

質量で重み付けされた粒子の質量中心を計算します。

`center`、`pos_center`、`mass_center`、および `median` の間には違いがあります：

  * `center`: 粒子のボックス中心
  * `pos_center`: 粒子の平均位置
  * `mass_center`: 粒子の質量加重平均位置
  * `median`: 粒子の位置の中央値
