```
integrate(u::GridData,g::PhysicalGrid)
```

グリッドデータ `u` の離散積分を、グリッド `g` のセル体積を使用して計算します。`u` が `VectorData` の場合、これは各座標方向の積分のベクトルを返します。
