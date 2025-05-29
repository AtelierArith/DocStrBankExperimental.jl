```
integral(p::VoronoiPolygon, val::Float64, taylor::SVector)::Float64
```

ポリゴン `p` 上の多項式の積分を計算します。`val` は `p.x` での値を定義し、テイラー展開 `taylor` を使用します。
