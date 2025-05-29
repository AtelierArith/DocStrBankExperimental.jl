```
MatDeforElastOrtho(
    mr::Type{MR},
    mass_density::N,
    E::N,
    nu::N,
    CTE::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

本当に等方的な弾性異方性材料を作成します。

質量密度、弾性および熱膨張特性の指定のみの便利なバージョン。
