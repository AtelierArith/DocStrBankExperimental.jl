```
set_polygon_hole!(poly :: Polygon_pslg, h :: AbstractArray{Float64,2})
```

`poly.hole`を適切に設定します。入力は`n_hole`-by-`2`の次元を持たなければなりません。

!!!     各穴はセグメントで囲まれている必要があります。セグメント上に穴を置かないでください。
