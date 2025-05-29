```
abstract type Q1P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Continuous piecewise first-order polynomials on simplices and quads, can be used for mixed geometries.

allowed ElementGeometries:

  * Edge1D (P1 space)
  * Triangle2D (P1 space)
  * Quadrilateral2D (Q1 space)
  * Tetrahedron3D (P1 space)
  * Hexahedron3D (Q1 space)
