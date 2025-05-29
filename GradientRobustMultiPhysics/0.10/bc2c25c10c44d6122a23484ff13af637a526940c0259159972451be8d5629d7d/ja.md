```
abstract type H1P2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

連続的な区分二次多項式。

許可される ElementGeometries:

  * Edge1D (二次多項式)
  * Triangle2D (二次多項式)
  * Quadrilateral2D (Q2 空間)
  * Tetrahedron3D (二次多項式)
