```
rotation_measure(n_cm3::Real, B_los::Real, dz::Real; ν_obs=nothing)
```

LOSに沿った平行磁場の回転測定を計算します。

## 引数

  * `n_cm3::Real`: [cm^-3]での電子数密度。
  * `B_los::Real`: [G]でのLOSに沿った磁場強度。

## 戻り値

  * `RM::Real`: [rad/m^2]での回転測定。

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`
