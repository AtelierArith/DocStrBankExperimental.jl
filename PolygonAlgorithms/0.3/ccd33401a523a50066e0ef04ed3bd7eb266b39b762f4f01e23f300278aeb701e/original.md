```
intersect_convex(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=ChasingEdgesAlg())
```

Find the intersection points of convex polygons `polygon1` and `polygon2`. They are not guaranteed to be unique.

A major assumption is that convex polygons only have one area of intersection. This fails in the general case with non-convex polygons.  See `intersect_geometry` for a more general `O(nm)` algorithm.

`alg` can either be `ChasingEdgesAlg()`, `MartinezRuedaAlg()`, `PointSearchAlg()` or `WeilerAthertonAlg()`. The two general algorithms `MartinezRuedaAlg` and `WeilerAthertonAlg` will throw an error if more than one area of intersection is found.
