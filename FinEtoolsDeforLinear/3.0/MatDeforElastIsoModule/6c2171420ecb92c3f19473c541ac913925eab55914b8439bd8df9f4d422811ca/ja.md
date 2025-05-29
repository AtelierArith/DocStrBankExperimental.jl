```
MatDeforElastIso(
    mr::Type{MR},
    mass_density::N,
    E::N,
    nu::N,
    CTE::N,
) where {MR<:AbstractDeforModelRed,N<:Number}
```

等方性弾性材料を作成し、すべての材料パラメータを提供します。

## 引数

  * `mr::Type{MR}`: 変形モデルのタイプ。
  * `mass_density::N`: 材料の質量密度。
  * `E::N`: 材料のヤング率。
  * `nu::N`: 材料のポアソン比。
  * `CTE::N`: 材料の熱膨張係数。
