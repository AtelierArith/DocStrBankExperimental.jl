```
abstract type HCURLN1{edim} <: AbstractHcurlFiniteElement where {edim<:Int}
```

Hcurlに準拠したベクトル値（ncomponents = edim）ネデレック空間の第一種および一次。

許可されるElementGeometries:

  * Triangle2D
