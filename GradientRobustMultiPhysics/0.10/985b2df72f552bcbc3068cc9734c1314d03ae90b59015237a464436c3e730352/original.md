```
abstract type H1P2B{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

Continuous piecewise second-order polynomials.

allowed ElementGeometries:

  * Triangle2D
