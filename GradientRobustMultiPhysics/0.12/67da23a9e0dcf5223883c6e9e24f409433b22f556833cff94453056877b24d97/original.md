```
abstract type H1P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Continuous piecewise first-order linear polynomials.

allowed ElementGeometries:

  * Edge1D
  * Triangle2D
  * Tetrahedron3D
