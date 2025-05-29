```julia
center(
    a::Array{T<:Union{PhysicalParticles.AbstractParticle2D, PhysicalParticles.AbstractPoint2D}, N}
) -> Any

```

点または粒子のボックス中心を計算します

`center`、`pos_center`、`mass_center`、および `median` の間には違いがあります：

  * `center`: 粒子のボックス中心
  * `pos_center`: 粒子の平均位置
  * `mass_center`: 粒子の質量加重平均位置
  * `median`: 粒子の位置の中央値
