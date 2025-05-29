```
抽象型 H1PK{ncomponents,edim,order} <: AbstractH1FiniteElement where {ncomponents<:Int,edim<:Int,order<:Int}
```

任意の次数 >= 1 の連続的な区分多項式で、edim 空間次元に ncomponents コンポーネントを持ちます。

許可される ElementGeometries:

  * Edge1D
  * Triangle2D
