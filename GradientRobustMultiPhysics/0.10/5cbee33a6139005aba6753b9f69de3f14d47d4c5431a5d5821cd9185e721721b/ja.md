```
abstract type H1MINI{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

ミニ有限要素。

許可される要素の幾何学:

  * Triangle2D (線形多項式 + 立方体セルバブル)
  * Quadrilateral2D (Q1空間 + 四次セルバブル)
  * Tetrahedron3D (線形多項式 + 立方体セルバブル)
