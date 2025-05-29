```
intersect_geometry(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=MartinezRuedaAlg())
```

General case of polygon intersection. 

`alg` can either be `MartinezRuedaAlg()` or `WeilerAthertonAlg()`. There are slight differences in the result depending on the algorithm. The `WeilerAthertonAlg` tends to be more robust to numeric inaccuracies.

Use `intersect_convex` for convex polygons for an `O(n+m)` algorithm.
