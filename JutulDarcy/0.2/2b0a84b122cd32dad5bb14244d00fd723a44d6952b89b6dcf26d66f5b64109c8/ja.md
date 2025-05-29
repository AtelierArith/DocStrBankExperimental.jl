```
setup_vertical_well(g, K, i, j; heel = 1, toe = grid_dims_ijk(g)[3], kwarg...)
```

与えられたグリッド `g` と透過性 `K` に対して、論理インデックス `i, j` で垂直井戸を設定し、k-論理インデックス `heel` から `toe` までのすべてのセルを貫通します。
