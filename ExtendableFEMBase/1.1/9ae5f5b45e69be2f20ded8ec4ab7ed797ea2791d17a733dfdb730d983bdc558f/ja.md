```
abstract type HDIVBDM2{edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

Hdiv適合のベクトル値（ncomponents = edim）Brezzi-Douglas-Marini空間の次数2

許可されるElementGeometries:

  * Triangle2D
