```
abstract type H1Q2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise second-order polynomials on simplices and quads. Can be used with mixed geometries (in 2D).

allowed ElementGeometries:

  * Edge1D (P2 space)
  * Triangle2D (P2 space)
  * Quadrilateral2D (Q2 space with cell bubble)
  * Tetrahedron3D (P2 space)
