```
integrate(u::PointData,ds::ScalarData)
```

データ `u` の離散表面積分を、`ds` の表面要素面積を使用して計算します。これは台形法の数値積分を使用します。`u` が `VectorData` の場合、これは各座標方向の積分のベクトルを返します。
