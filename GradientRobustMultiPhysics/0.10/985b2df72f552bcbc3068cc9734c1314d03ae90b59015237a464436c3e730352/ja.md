```
abstract type H1P2B{ncomponents,edim} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int}
```

連続的な区分的二次多項式。

許可される ElementGeometries:

  * Triangle2D
