```
count = point_to_nearest_grid(pt_x,pt_y,pt_z, X,Y,Z; radius_factor=1)
```

これは、最近傍補間を使用して、3Dグリッド点が指定された `X`,`Y`,`Z` 3D座標配列の近くにあるポイント（`pt_x`,`pt_y`,`pt_z` 座標ベクトルで与えられる）の数をカウントします。間隔は `(Δx,Δy,Δz)` で、検索半径は `R=radius_factor*(Δx² + Δy² + Δz²)^(1/3)` です。
