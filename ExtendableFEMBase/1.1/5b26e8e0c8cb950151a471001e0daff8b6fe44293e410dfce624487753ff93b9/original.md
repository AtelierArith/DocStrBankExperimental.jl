```
abstract type L2P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Discontinuous piecewise first-order linear polynomials (same as H1P1 but enforces broken = true).

allowed ElementGeometries:

  * Edge1D
  * Triangle2D
  * Tetrahedron3D
