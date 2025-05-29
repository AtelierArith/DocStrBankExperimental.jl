```
traverse!(a::AbstractArray, c::GeometryStructure, level=1)
```

与えられた座標系に対して、その参照を再帰的にたどり、他の座標系を見つけて配列 `a` にいくつかのタプル `(level, c)` を追加します。`level` は座標系が見つかった深さに対応し、`c` は見つかった座標系です。
