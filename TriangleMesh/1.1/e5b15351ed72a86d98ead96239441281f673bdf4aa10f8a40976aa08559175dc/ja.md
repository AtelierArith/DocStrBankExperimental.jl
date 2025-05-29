```
set_polygon_segment_marker!(poly :: Polygon_pslg, sm :: AbstractArray{Int,1})
```

`poly.segment_marker`を適切に設定します。入力は`n_segment`-by-`1`の次元を持つ必要があります。そうでない場合、すべてのセグメントのマーカーは1に設定されます。
