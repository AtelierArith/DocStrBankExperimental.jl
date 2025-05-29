```
boundary_condition_slip_wall(u_inner, orientation_or_normal, direction, x, t, surface_flux_function, eq::BloodFlowEquations1D)
```

スリップ壁境界条件を実装し、速度の法線成分が反射されます。

### パラメータ

  * `u_inner`: 境界近くの領域内の状態ベクトル。
  * `orientation_or_normal`: 境界の法線方向。
  * `direction`: 境界の方向を示す整数。
  * `x`: 位置ベクトル。
  * `t`: 時間。
  * `surface_flux_function`: 境界でのフラックスを計算する関数。
  * `eq`: `BloodFlowEquations1D`のインスタンス。

### 戻り値

スリップ壁で計算された境界フラックス。
