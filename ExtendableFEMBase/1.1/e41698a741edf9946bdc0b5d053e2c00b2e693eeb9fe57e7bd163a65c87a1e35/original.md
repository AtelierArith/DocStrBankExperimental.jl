```
abstract type H1P2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise second-order polynomials.

allowed ElementGeometries:

  * Edge1D
  * Triangle2D
  * Tetrahedron3D
