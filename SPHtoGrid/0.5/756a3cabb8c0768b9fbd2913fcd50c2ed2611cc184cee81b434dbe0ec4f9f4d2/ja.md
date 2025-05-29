```
rotation_measure(n_cm3::Real, B_los::Real, dz::Real, ν_obs::Real)
```

与えられた周波数でのLOSに沿った平行磁場の回転測定を計算します。LOSに沿った偏光放射の連続回転に使用されます。

## 引数

  * `n_cm3::Real`: [cm^-3]での電子数密度。
  * `B_los::Real`: [G]でのLOSに沿った磁場強度。
  * `dz::Real`: [cm]でのLOSに沿った深さ。便利なヘルパー関数については[`get_dz`](@ref)を参照してください。
  * `ν_obs::Real`: [Hz]での観測周波数。

## 戻り値

  * `RM::Real`: [rad/cm^2]での回転測定。

## マッピング設定

  * 重み関数: [`part_weight_physical`](@ref)
  * 画像を縮小: `false`
  * ストークス: `true`
  * sort_z: `true`
  * `RM`: この関数の出力を使用します。
