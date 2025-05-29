```
abstract type HDIVRT1{edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

Hdiv-conforming vector-valued (ncomponents = edim) Raviart-Thomas space of order 1.

allowed ElementGeometries:

  * Triangle2D
  * Tetrahedron3D
