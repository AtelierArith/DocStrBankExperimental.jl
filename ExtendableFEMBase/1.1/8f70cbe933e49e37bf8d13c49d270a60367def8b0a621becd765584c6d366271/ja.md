```
abstract type H1Q2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

単純体および四角形上の連続的な区分的二次多項式。混合幾何学（2D）で使用できます。

許可される ElementGeometries:

  * Edge1D (P2 空間)
  * Triangle2D (P2 空間)
  * Quadrilateral2D (セルバブルを持つ Q2 空間)
  * Tetrahedron3D (P2 空間)
