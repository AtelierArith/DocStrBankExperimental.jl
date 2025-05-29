```
abstract type H1CR{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Crouzeix-Raviart element (only continuous at face centers).

allowed ElementGeometries:

  * Triangle2D (piecewise linear, similar to P1)
  * Quadrilateral2D (similar to Q1 space)
  * Tetrahedron3D (piecewise linear, similar to P1)
