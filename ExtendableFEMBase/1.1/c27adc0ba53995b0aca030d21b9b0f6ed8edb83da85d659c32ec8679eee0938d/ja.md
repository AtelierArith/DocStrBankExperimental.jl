```
abstract type HDIVRTk{edim, order} <: AbstractHdivFiniteElement where {edim<:Int}
```

任意の次数のHdiv準拠ベクトル値（ncomponents = edim）Raviart-Thomas空間。

許可されるElementGeometries:

  * Triangle2D
