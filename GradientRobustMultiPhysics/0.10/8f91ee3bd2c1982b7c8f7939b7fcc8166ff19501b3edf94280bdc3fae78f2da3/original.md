```
abstract type HCURLN0{edim} <: AbstractHcurlFiniteElement where {edim<:Int}
```

Hcurl-conforming vector-valued (ncomponents = edim) lowest-order Nedelec space.

allowed ElementGeometries:

  * Triangle2D
  * Quadrilateral2D
  * Tetrahedron3D
