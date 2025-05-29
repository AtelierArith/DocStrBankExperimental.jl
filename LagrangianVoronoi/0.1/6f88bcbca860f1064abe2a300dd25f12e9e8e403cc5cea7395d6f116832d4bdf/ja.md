```
point_value(grid::VoronoiGrid, x::RealVector, fun::Function)
```

多角形上で定義された関数 `fun` の補間を任意の点 `x` で取得します。これは遅いコードであり、パフォーマンスが重要な領域では決して使用すべきではありません。
