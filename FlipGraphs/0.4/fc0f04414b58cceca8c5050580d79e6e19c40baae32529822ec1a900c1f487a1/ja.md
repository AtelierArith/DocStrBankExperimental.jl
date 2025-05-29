```
triangulated_polygon(n::Integer) :: TriangulatedPolygon
```

凸の `n`-角形を三角形分割します。

頂点は1から `n` まで反時計回りに名前が付けられます。内部はジグザグパターンで三角形分割されます。
