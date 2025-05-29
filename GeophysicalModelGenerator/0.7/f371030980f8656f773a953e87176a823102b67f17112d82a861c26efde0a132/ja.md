```
Grid_counts = point_to_nearest_grid(pt_x,pt_y,pt_z, Grid::CartData; radius_factor=1)
```

最近傍補間を使用して、3D `CartGrid`によって指定された`Grid`の近くにあるポイントの数をカウントします（`pt_x`、`pt_y`、`pt_z`座標ベクトルによって与えられます）。検索半径は`R=radius_factor*(Δx² + Δy² + Δz²)^(1/3)`です。

`Grid_counts`は`Grid`ですが、ヒット数を持つ追加のフィールド`Count`があります。
