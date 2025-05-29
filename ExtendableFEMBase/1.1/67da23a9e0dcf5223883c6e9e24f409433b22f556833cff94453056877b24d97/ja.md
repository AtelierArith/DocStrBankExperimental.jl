```
abstract type H1P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

連続的な区分的一次線形多項式。

許可される ElementGeometries:

  * Edge1D
  * Triangle2D
  * Tetrahedron3D
