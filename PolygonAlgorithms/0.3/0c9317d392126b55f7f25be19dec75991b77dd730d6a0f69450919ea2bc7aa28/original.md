```
xor_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=WeilerAthertonAlg())
```

General case of polygon xor: in one polygon or the other but not both. Possibly returns holes but does not classify them as holes.

`alg` can only be `MartinezRuedaAlg()`.
