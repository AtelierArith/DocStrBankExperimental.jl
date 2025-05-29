```
difference_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=WeilerAthertonAlg())
```

General case of polygon difference: points in `polygon1` that are not in `polygon2`.

`alg` can only be `MartinezRuedaAlg()`.
