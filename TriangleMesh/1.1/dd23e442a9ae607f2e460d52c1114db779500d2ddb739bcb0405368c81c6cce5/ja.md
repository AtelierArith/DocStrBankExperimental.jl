```
set_polygon_point_marker!(poly :: Polygon_pslg, pm :: AbstractArray{Int,2})
```

`poly.point_marker`を適切に設定します。入力は`n_point`×`n_point_marker`の次元を持たなければなりません。`n_point_marker`は1または0であることができます。
