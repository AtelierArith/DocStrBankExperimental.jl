```
intersect_convex(polygon1::Vector{<:Point2D}, polygon2::Vector{<:Point2D}, alg=ChasingEdgesAlg())
```

凸多角形 `polygon1` と `polygon2` の交点を見つけます。交点が一意であることは保証されていません。

主な仮定は、凸多角形は交差領域が1つだけであるということです。これは、非凸多角形の場合には一般的なケースでは失敗します。より一般的な `O(nm)` アルゴリズムについては `intersect_geometry` を参照してください。

`alg` は `ChasingEdgesAlg()`、`MartinezRuedaAlg()`、`PointSearchAlg()` または `WeilerAthertonAlg()` のいずれかにすることができます。一般的な2つのアルゴリズムである `MartinezRuedaAlg` と `WeilerAthertonAlg` は、交差領域が2つ以上見つかった場合にエラーをスローします。
