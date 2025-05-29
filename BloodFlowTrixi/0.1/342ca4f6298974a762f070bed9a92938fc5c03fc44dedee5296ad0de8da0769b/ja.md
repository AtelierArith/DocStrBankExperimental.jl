```
boundary_condition_pressure_in(u_inner, normal, x, t, surface_flux_function, eq::BloodFlowEquations2D)
```

2D血流モデルに対して、指定された圧力の流入境界条件を適用します。このバージョンでは特定の方向パラメータは使用されません。

### パラメータ

  * `u_inner`: 境界での内部状態ベクトル。
  * `normal`: 境界方向を示す法線ベクトル。
  * `x`: 境界での位置ベクトル。
  * `t`: 時間値。
  * `surface_flux_function`: 表面フラックスを計算する関数。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。

### 戻り値

`SVector`としての境界フラックス。
