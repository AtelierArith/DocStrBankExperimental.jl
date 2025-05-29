```
abstract type H1CR{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

Crouzeix-Raviart要素（面の中心でのみ連続）。

許可されるElementGeometries:

  * Triangle2D（部分線形、P1に類似）
  * Quadrilateral2D（Q1空間に類似）
  * Tetrahedron3D（部分線形、P1に類似）
