```
MatDeforElastIso(
    mr::Type{MR},
    E::N,
    nu::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

デフォルトの質量密度と熱膨張を持つ等方性弾性材料を作成します。
