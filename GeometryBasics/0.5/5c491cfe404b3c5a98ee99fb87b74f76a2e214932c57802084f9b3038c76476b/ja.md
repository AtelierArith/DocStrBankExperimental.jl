```
connect(points::AbstractVector{<: Point}, P::Type{<: Polytope{N}}, skip::Int = N)
```

複数の点をポリトープ `P` に接続するビューを作成します。各ポリトープの間で、次が始まるまで `skip` 要素がスキップされます。例: `julia x = connect(Point[(1, 2), (3, 4), (5, 6), (7, 8)], Line, 2) x == [Line(Point(1, 2), Point(3, 4)), Line(Point(5, 6), Point(7, 8))]`
