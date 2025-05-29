```
abstract type H1P3{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise third-order polynomials.

allowed ElementGeometries:

  * Edge1D
  * Triangle2D
  * Tetrahedron3D
