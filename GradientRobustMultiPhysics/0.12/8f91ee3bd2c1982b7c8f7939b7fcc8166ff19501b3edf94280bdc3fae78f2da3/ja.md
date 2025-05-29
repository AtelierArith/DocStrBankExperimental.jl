```
abstract type HCURLN0{edim} <: AbstractHcurlFiniteElement where {edim<:Int}
```

Hcurl適合のベクトル値（ncomponents = edim）最低次のNedelec空間。

許可されるElementGeometries:

  * Triangle2D
  * Quadrilateral2D
  * Tetrahedron3D
