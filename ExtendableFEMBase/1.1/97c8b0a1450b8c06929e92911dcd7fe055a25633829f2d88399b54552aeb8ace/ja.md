```
abstract type HCURLN0{edim} <: AbstractHcurlFiniteElement where {edim<:Int}
```

Hcurlに準拠したベクトル値（ncomponents = edim）の最下位のネデレック空間の第一種。

許可されるElementGeometries:

  * Triangle2D
  * Quadrilateral2D
  * Tetrahedron3D
