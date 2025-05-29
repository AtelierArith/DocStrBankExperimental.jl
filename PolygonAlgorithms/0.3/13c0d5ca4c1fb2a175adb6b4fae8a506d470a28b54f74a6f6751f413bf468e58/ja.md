```
intersect_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=MartinezRuedaAlg())
```

多角形の交差の一般的なケース。

`alg` は `MartinezRuedaAlg()` または `WeilerAthertonAlg()` のいずれかです。アルゴリズムによって結果にわずかな違いがあります。`WeilerAthertonAlg` は数値的不正確さに対してより堅牢である傾向があります。

凸多角形には `O(n+m)` アルゴリズムのために `intersect_convex` を使用してください。
