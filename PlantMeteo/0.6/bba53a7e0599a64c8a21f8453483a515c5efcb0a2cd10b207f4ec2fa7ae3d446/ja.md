大気の構造は、気象/大気に関連するすべての値を保持します。

# 引数

  * `date<:AbstractDateTime = Dates.now()`: 記録の日付。
  * `duration<:Period = Dates.Second(1.0)`: Dates.Periodでの時間ステップの期間。
  * `T` (°C): 空気温度
  * `Wind` (m s-1): 風速
  * `Rh` (0-1): 相対湿度（`rh_from_vpd`を使用して計算できます）
  * `P = DEFAULTS.P` (kPa): 空気圧。デフォルト値は1 atm、*すなわち* 地球の平均海面大気圧です。
  * `Precipitations = DEFAULTS.Precipitations` (mm): 大気からの降水量（*すなわち* 雨、雪、雹など）
  * `Cₐ = DEFAULTS.Cₐ` (ppm): 空気中のCO₂濃度
  * `check = true`: 入力値の有効性をチェックするかどうか。
  * `e = vapor_pressure(T,Rh)` (kPa): 水蒸気圧
  * `eₛ = e_sat(T)` (kPa): 飽和水蒸気圧
  * `VPD = eₛ - e` (kPa): 水蒸気圧不足
  * `ρ = air_density(T, P, constants.Rd, constants.K₀)` (kg m-3): 空気密度
  * `λ = latent_heat_vaporization(T, constants.λ₀)` (J kg-1): 蒸発潜熱
  * `γ = psychrometer_constant(P, λ, constants.Cₚ, constants.ε)` (kPa K−1): サイクロメーターの「定数」
  * `ε = atmosphere_emissivity(T,e,constants.K₀)` (0-1): 大気の放射率
  * `Δ = e_sat_slope(meteo.T)` (0-1): 空気温度における飽和水蒸気圧の傾き
  * `clearness::A = Inf` (0-1): 空の明るさ
  * `Ri_SW_f::A = Inf` (W m-2): 入射短波放射フラックス
  * `Ri_PAR_f::A = Inf` (W m-2): 入射PARフラックス
  * `Ri_NIR_f::A = Inf` (W m-2): 入射NIRフラックス
  * `Ri_TIR_f::A = Inf` (W m-2): 入射TIRフラックス
  * `Ri_custom_f::A = Inf` (W m-2): カスタム波長帯の入射放射フラックス

# 注意事項

この構造は、`T`、`Rh`、`Wind`、および`P`のみを使用して構築できます。他のすべての変数はオプションであり、デフォルト値のままにするか、`Arguments`で指定された関数を使用して自動的に計算されます。

# 例

```julia
Atmosphere(T = 20.0, Wind = 1.0, P = 101.3, Rh = 0.65)
```
