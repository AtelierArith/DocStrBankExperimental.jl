```
coordinates(p::PointCloud, index; crs)
```

`index`-番目の点のx、y、z座標を`Float64`のタプルとして取得します。異なるcrsが指定されない限り、`PointCloud`の座標参照系（CRS）が使用されます。複数の点の座標を取得するには、`index`引数にインデックスの範囲や`:`を渡します。

現在の`PointCloud`のCRSではなく、新しいCRSに座標を変換するには、`crs`キーワード引数を提供します。
