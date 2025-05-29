```
abstract type H1Q2{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

連続的な区分的二次多項式。

許可される ElementGeometries:

  * Edge1D (二次多項式)
  * Triangle2D (二次多項式)
  * Quadrilateral2D (セルバブルを持つQ2空間)
  * Tetrahedron3D (二次多項式)
