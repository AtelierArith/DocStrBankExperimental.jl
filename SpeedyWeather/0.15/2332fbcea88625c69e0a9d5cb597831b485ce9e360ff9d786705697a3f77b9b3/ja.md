水の飽和蒸気圧をクラウジウス・クラペイロン方程式を用いて計算するためのパラメータ、

```
e(T) = e₀ * exp( -Lᵥ/Rᵥ * (1/T - 1/T₀)),
```

ここで、Tはケルビン、Lᵥは凝縮の潜熱、Rᵥは水蒸気の気体定数です。

  * `e₀::AbstractFloat`: 0°Cにおける飽和水蒸気圧 [Pa]
  * `T₀::AbstractFloat`: 0°Cのケルビン
  * `Lᵥ::AbstractFloat`: 水の凝縮/蒸発の潜熱 [J/kg]
  * `cₚ::AbstractFloat`: 定圧での比熱 [J/K/kg]
  * `R_vapour::AbstractFloat`: 水蒸気の気体定数 [J/kg/K]
  * `R_dry::AbstractFloat`: 乾燥空気の気体定数 [J/kg/K]
  * `Lᵥ_Rᵥ::AbstractFloat`: 潜熱を水蒸気の気体定数で割った値 [K]
  * `T₀⁻¹::AbstractFloat`: T₀の逆数、0°Cのケルビンの逆数
  * `mol_ratio::AbstractFloat`: 水蒸気と乾燥空気の分子量の比 [1](=R*dry/R*vapour)。
