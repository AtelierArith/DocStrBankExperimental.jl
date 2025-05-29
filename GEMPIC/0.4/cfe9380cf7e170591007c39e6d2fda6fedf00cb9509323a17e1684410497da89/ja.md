```
HamiltonianSplittingBoris( maxwell_solver,
                           kernel_smoother_0, kernel_smoother_1,
                           particle_group,
                           e_dofs_1, e_dofs_2, b_dofs)
```

GEMPICフレームワークにおけるボリスプッシャー（スプライン有限要素）

  * `mid` は時間 $t_{n+1/2}$ における磁場を表し（プッシュに使用）
  * `j_dofs` は電流密度のカーネル表現のためのもの。
  * `maxwell_solver`    : マクスウェルソルバー
  * `kernel_smoother_0` : カーネルスムーザー
  * `kernel_smoother_1` : カーネルスムーザー
  * `particle_group`    : 粒子グループ
  * `efield_dofs`       : 電場の係数のための配列
  * `bfield_dofs`       : 磁場の係数のための配列
  * `x_min`             : x領域の下限
  * `Lx`                : x方向の領域の長さ。
