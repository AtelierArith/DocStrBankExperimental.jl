```
abstract type HDIVBDM2{edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

Hdiv-conforming vector-valued (ncomponents = edim) Brezzi-Douglas-Marini space of order 2

allowed ElementGeometries:

  * Triangle2D
