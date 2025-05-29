```
FluxLMARS(c)(u_ll, u_rr, orientation_or_normal_direction,
             equations::CompressibleEulerEquations2D)
```

大気の流れに対する低マッハ数近似リーマンソルバー (LMARS) で、音速の推定値 `c` を使用します。

参考文献:

  * Xi Chen et al. (2013) 垂直ラグランジュ座標を用いた圧縮性オイラー方程式の制御体積モデル [DOI: 10.1175/MWR-D-12-00129.1](https://doi.org/10.1175/mwr-d-12-00129.1)
