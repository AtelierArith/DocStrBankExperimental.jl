```
abstract type H1P2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise second-order polynomials.

allowed ElementGeometries:

  * Edge1D (quadratic polynomials)
  * Triangle2D (quadratic polynomials)
  * Quadrilateral2D (Q2 space)
  * Tetrahedron3D (quadratic polynomials)
