```
abstract type HDIVRTk{edim, order} <: AbstractHdivFiniteElement where {edim<:Int}
```

Hdiv-conforming vector-valued (ncomponents = edim) Raviart-Thomas space of arbitrary order.

allowed ElementGeometries:

  * Triangle2D
