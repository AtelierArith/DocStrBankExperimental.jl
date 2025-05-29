```
abstract type L2P1{ncomponents} <: AbstractH1FiniteElement where {ncomponents<:Int}
```

不連続な区分的一次線形多項式（H1P1と同じですが、broken = trueを強制します）。

許可されるElementGeometries:

  * Edge1D
  * Triangle2D
  * Tetrahedron3D
