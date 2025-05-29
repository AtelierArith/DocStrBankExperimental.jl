```
abstract type H1PK{ncomponents,edim,order} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int,order<:Int}
```

任意の次数 >= 1 の連続的な区分多項式。

許可される ElementGeometries:

  * Edge1D
  * Triangle2D
