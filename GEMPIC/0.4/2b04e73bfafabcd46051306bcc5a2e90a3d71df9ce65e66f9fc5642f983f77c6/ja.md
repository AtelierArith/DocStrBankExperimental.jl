```
maxwell_solver = MaxwellFEM1D( mesh, degree )
```

周期的グリッド上の1Dマクスウェルスプライン有限要素ソルバー

  * `Lx`                   : 周期的領域の長さ
  * `delta_x`              : セルサイズ
  * `n_dofs`               : セルの数（およびグリッドポイント）
  * `s_deg_0`              : スプライン次数0-形式
  * `s_deg_1`              : スプライン次数1-形式
  * `mass_0`               : 0-形式質量行列の係数
  * `mass_1`               : 1-形式質量行列の係数
  * `eig_mass0`            : 循環0-形式質量行列の固有値
  * `eig_mass1`            : 循環1-形式質量行列の固有値
  * `eig_weak_ampere`      : アンペールのための循環更新行列の固有値
  * `eig_weak_poisson`     : ポアソンのための循環更新行列の固有値
  * `plan_fw`              : fftプラン（前方）
  * `plan_bw`              : fftプラン（後方）
