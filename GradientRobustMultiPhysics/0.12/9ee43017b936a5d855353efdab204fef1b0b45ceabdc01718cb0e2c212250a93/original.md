```
abstract type HDIVRT0{edim} <: AbstractHdivFiniteElement where {edim<:Int}
```

Hdiv-conforming vector-valued (ncomponents = edim) lowest-order Raviart-Thomas space.

allowed ElementGeometries:

  * Triangle2D
  * Quadrilateral2D
  * Tetrahedron3D
  * Hexahedron3D
