```
boundary_condition_outflow(u_inner, orientation_or_normal, x, t, surface_flux_function, eq::BloodFlowEquations2D)
```

2D血流モデルのための流出境界条件を適用し、フラックスを反射しません。このバージョンは特定の方向パラメータを使用しません。

### パラメータ

  * `u_inner`: 境界での内部状態ベクトル。
  * `orientation_or_normal`: 境界方向を示すオリエンテーションインデックスまたは法線ベクトル。
  * `x`: 境界での位置ベクトル。
  * `t`: 時間値。
  * `surface_flux_function`: 表面フラックスを計算する関数。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。

### 戻り値

境界フラックスを`SVector`として返します。
