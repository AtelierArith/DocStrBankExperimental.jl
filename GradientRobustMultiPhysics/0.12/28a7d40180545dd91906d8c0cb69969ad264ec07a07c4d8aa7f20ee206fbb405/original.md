```
abstract type H1P3{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise third-order polynomials.

allowed ElementGeometries:

  * Edge1D (cubic polynomials)
  * Triangle2D (cubic polynomials, experimental)
