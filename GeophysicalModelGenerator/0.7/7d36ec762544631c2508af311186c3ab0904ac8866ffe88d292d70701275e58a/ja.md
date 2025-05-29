```
Grid_counts = point_to_nearest_grid(Point::GeoData, Grid::GeoData; radius_factor=1)
```

最近傍補間を使用して、3D `Grid` の近くにあるポイント（`Point` によって与えられる）の数をカウントします。検索半径は `R=radius_factor*(Δx² + Δy² + Δz²)^(1/3)` です。

`Point` は 1D 座標ベクトルを持っている必要があります。

`Grid_counts` は `Grid` ですが、ヒット数を持つ追加のフィールド `Count` があります。
