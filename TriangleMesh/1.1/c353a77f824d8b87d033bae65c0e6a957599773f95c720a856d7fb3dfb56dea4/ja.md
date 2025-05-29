```
set_polygon_region!(poly :: Polygon_pslg, h :: AbstractArray{Float64,2})
```

`poly.region`を適切に設定します。入力は`n_region`-by-`2`の次元を持たなければなりません。

!!!     各領域はセグメントで囲まれている必要があります。セグメント上に領域を配置しないでください。
