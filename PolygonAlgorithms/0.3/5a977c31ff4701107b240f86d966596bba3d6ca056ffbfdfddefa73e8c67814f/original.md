```
union_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=WeilerAthertonAlg())
```

General case of polygon union: in both polygons.  Possibly returns holes but does not classify them as holes.

`alg` can only be `MartinezRuedaAlg()`.
