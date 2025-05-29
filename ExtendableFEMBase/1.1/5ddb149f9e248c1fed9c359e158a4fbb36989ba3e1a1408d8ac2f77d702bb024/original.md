```
abstract type HCURLN1{edim} <: AbstractHcurlFiniteElement where {edim<:Int}
```

Hcurl-conforming vector-valued (ncomponents = edim) Nedelec space of first kind and order 1.

allowed ElementGeometries:

  * Triangle2D
