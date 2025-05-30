```
integrate(u::PointData,cache::BasicILMCache,i::Int)
```

スカラーデータ `u` の離散表面積分を、`cache` 内の浸漬点に対して、`cache` のボディリスト内のボディ `i` に対して計算します。これは台形法の数値積分を使用します。`u` が `VectorData` の場合、各座標方向の積分のベクトルを返します。この操作は、`cache` が `GridScaling` または `IndexScaling` のいずれに設定されていても、同じ効果を生み出します。どちらの場合でも、表面要素の面積が使用されます。
