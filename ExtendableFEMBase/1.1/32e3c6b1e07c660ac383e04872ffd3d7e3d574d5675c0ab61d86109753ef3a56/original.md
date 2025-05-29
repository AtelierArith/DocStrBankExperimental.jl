```
abstract type H1PK{ncomponents,edim,order} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int,order<:Int}
```

Continuous piecewise polynomials of arbitrary order >= 1 with ncomponents components in edim space dimensions.

allowed ElementGeometries:

  * Edge1D
  * Triangle2D
