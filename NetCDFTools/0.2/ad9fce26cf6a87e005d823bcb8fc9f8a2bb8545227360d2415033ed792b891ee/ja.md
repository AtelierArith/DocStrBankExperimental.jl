```
weight_idw(point::Tuple, sites::AbstractMatrix; r_deg=5, nmax::Int=20, m=2)
weight_adw(point::Tuple, sites::AbstractMatrix; r_deg=5, nmax::Int=20, m=4, cdd=450)
```

# 引数

  * `point`: (経度, 緯度) 座標のタプル
  * `sites`: (経度, 緯度) 座標の行列
  * `r_deg`: 半径（度単位）
  * `nmax`: 最大サイト数
  * `m`: 距離の累乗
