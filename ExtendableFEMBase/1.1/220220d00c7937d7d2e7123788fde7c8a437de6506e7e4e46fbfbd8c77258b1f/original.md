```
abstract type HDIVBDM1{edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

Hdiv-conforming vector-valued (ncomponents = edim) lowest-order Brezzi-Douglas-Marini space

allowed ElementGeometries:

  * Triangle2D
  * Quadrilateral2D
  * Tetrahedron3D
