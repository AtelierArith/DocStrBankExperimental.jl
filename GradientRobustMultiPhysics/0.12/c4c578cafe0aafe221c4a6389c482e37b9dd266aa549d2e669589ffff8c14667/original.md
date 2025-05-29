```
abstract type H1Q2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise second-order polynomials.

allowed ElementGeometries:

  * Edge1D (quadratic polynomials)
  * Triangle2D (quadratic polynomials)
  * Quadrilateral2D (Q2 space with cell bubble)
  * Tetrahedron3D (quadratic polynomials)
