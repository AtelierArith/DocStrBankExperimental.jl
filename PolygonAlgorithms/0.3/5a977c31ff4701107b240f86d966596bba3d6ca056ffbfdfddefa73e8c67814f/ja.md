```
union_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=WeilerAthertonAlg())
```

多角形の和の一般的なケース：両方の多角形において。穴を返す可能性がありますが、それらを穴として分類することはありません。

`alg` は `MartinezRuedaAlg()` のみ使用できます。
