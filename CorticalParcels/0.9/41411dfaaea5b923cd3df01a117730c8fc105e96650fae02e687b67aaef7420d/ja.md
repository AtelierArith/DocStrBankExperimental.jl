```
 distance(p1, p2; method = CentroidToCentroid())
```

`Parcel`の`p1`と`p2`の間の距離を`method`（`CentroidToCentroid()`または`ClosestVertices`のいずれか）を使用して求めます。このメソッド呼び出しは、最初のパーセルの`SurfaceSpace`構造体に属する距離行列`:distances`を見つけることを期待します。
