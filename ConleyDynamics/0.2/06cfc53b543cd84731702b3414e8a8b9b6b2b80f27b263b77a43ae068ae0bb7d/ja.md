```
manifold_boundary(lc::LefschetzComplex)
```

Lefschetz複体から多様体の境界を抽出します。

この関数は、境界を持つコンパクトなd次元多様体を表すLefschetz複体を期待します。多様体の位相的境界にあるすべてのセルのリストを`Vector{Int}`の形式で返します。
