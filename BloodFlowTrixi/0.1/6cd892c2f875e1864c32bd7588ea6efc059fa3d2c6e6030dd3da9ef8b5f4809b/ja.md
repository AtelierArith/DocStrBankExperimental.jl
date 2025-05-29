```
boundary_condition_outflow(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations2D)
```

2D血流モデルのための流出境界条件を適用し、フラックスを反射しません。

### パラメータ

  * `u_inner`: 境界での内部状態ベクトル。
  * `orientation_or_normal`: 境界方向を示すオリエンテーションインデックスまたは法線ベクトル。
  * `direction`: 空間方向を示すインデックス（( \theta )-方向の場合は1、その他は(s)-方向）。
  * `x`: 境界での位置ベクトル。
  * `t`: 時間値。
  * `surface_flux_function`: 表面フラックスを計算する関数。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。

### 戻り値

`SVector`としての境界フラックス。
