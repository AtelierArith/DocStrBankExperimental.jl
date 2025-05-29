```
abstract type Q1P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

単純体および四角形上の連続的な区分的1次多項式で、混合幾何学に使用できます。

許可される ElementGeometries:

  * Edge1D (P1 空間)
  * Triangle2D (P1 空間)
  * Quadrilateral2D (Q1 空間)
  * Tetrahedron3D (P1 空間)
  * Hexahedron3D (Q1 空間)
