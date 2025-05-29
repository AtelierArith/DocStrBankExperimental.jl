```
integrate(u::GridData,cache::BasicILMCache)
```

グリッドデータ `u` の離散体積積分を計算します。`u` が `VectorGridData` の場合、これは各座標方向の積分のベクトルを返します。この積分は、`GridScaling` または `IndexScaling` が使用されているかどうかに関わらず、同じ結果を生成します。
