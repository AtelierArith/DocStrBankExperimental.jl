```
abstract type Q1P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Continuous piecewise first-order polynomials on quads.

allowed ElementGeometries:

  * Quadrilateral2D (Q1 space)
  * Hexahedron3D (Q1 space)
