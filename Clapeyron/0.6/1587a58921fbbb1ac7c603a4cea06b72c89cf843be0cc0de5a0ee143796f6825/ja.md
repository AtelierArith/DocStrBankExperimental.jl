```
ReferenceState(type::Symbol = :no_set;T0 = NaN;P0 = NaN,H0 = NaN,S0 = NaN,phase = :unknown,z0 = Float64[])
```

エンタルピーとエントロピーの基準状態を定義するために使用されるパラメータで、通常は理想モデルに保存されます。設定されると、指定された点でのエントロピーとエンタルピーが固定されるように `a0` と `a1` の値のセットを計算します。

`type` 引数は以下の独立したオプションを受け入れます：

  * `:no_set`: 状態方程式によって確立された現在のデフォルトを返します。
  * `:ashrae`: h = s = 0 at -40°C 飽和液体
  * `:iir`: h = 200.0 kJ/kg, s=1.0 kJ/kg/K at 0C 飽和液体
  * `:nbp`: h = s = 0 at 1 atm 飽和液体
  * `:stp`: h = s = 0 at 1 bar, 0°C 最も安定した相の流体
  * `:stp_old`: h = s = 0 at 1 atm, 0°C 最も安定した相の流体
  * `:ntp`: h = s = 0 at 1 atm, 20°C 最も安定した相の流体

また、以下のオプションも受け入れますが、追加の仕様が必要です：

  * `:volume` h = H0, s = S0, at T = T0, v = `volume(model,P0,T0,z0,phase = phase)`
  * `:saturation_pressure` h = H0, s = S0, at T = T0, 飽和相（`phase` 引数で指定）
  * `:saturation_temperature` h = H0, s = S0, at p = P0, 飽和相（`phase` 引数で指定）

`z0` が指定されていない場合、基準状態の計算は各成分ごとに行われます。

## 例

```
julia> model = PCSAFT(["water","pentane"],idealmodel = ReidIdeal,reference_state = ReferenceState(:nbp))
PCSAFT{ReidIdeal, Float64} with 2 components:
 "water"
 "pentane"
Contains parameters: Mw, segment, sigma, epsilon, epsilon_assoc, bondvol

julia> model2 = PCSAFT(["water","pentane"],idealmodel = ReidIdeal,reference_state = :nbp) #equivalent
PCSAFT{ReidIdeal, Float64} with 2 components:
 "water"
 "pentane"
Contains parameters: Mw, segment, sigma, epsilon, epsilon_assoc, bondvol

julia> pure = split_model(model)
2-element Vector{PCSAFT{ReidIdeal, Float64}}:
 PCSAFT{ReidIdeal, Float64}("water")
 PCSAFT{ReidIdeal, Float64}("pentane")

julia> T,vl,_ = saturation_temperature(pure[1],101325.0) #saturated liquid at 1 atm
(373.2706553019503, 2.0512186595412677e-5, 0.03006573003253086)

julia> enthalpy(pure[1],101325.0,T)
-5.477897970382323e-6

julia> entropy(pure[1],101325.0,T)
5.009221069190994e-9
```
