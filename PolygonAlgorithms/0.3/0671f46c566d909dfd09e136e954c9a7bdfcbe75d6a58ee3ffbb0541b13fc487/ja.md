```
difference_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=WeilerAthertonAlg())
```

多角形の差の一般的なケース：`polygon1` にあり `polygon2` にない点。

`alg` は `MartinezRuedaAlg()` のみ使用できます。
