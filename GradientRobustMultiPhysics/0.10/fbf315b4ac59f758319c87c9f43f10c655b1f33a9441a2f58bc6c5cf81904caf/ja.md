```
abstract type Q1P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

四角形上の連続的な区分的一次多項式。

許可される ElementGeometries:

  * Quadrilateral2D (Q1 空間)
  * Hexahedron3D (Q1 空間)
