```
function median(a::Array{T}, symbol::Symbol) where T <: AbstractParticle
function median(d::Dict, symbol::Symbol)
```

配列の粒子または粒子の配列の辞書におけるフィールド `symbol` の中央値を返します。

`center`、`pos_center`、`mass_center` および `median` の間には違いがあります：

  * `center`: 粒子のボックス中心
  * `pos_center`: 粒子の平均位置
  * `mass_center`: 粒子の質量加重平均位置
  * `median`: 粒子の位置の中央値
