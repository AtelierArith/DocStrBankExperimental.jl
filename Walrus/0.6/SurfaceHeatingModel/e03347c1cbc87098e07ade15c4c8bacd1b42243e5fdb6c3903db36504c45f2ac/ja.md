```
SurfaceHeatExchange(; wind_stress,
                      air_temperature = 18, # °C
                      latent_heat_vaporisation = EmpiricalLatentHeatVaporisation(),
                      vapour_pressure = AugustRocheMagnusVapourPressure(),
                      water_specific_heat_capacity = 3991., # J / K / kg
                      water_density = 1026., # kg / m³
                      air_specific_heat_capacity = 1003.5, # J / K / kg
                      air_density = 1.204, # kg
                      air_water_mixing_ratio = 0.001, # kg / kg
                      stephan_boltzman_constant = 5.670374419e-8, # W / K⁴
                      ocean_emissivity = 0.97, #
                      downwelling_longwave = (T, args...)->60) # W
```

表面熱交換は次の形で指定されます：

$$
Q = Qᵢᵣ + Qₛ + Qₗ,
$$

ここで $Qᵢᵣ$ は長波（赤外線）放射による熱フラックス、$Qₛ$ は顕熱フラックス、$Qₗ$ は潜熱フラックスです。短波放射フラックスは、十分に水中に浸透するため、`HomogeneousBodyHeating` によって別途扱われると仮定されているため、ここでは無視されます（したがって、短波の浸透が適切に短いと仮定しています）。

短波項はステファン・ボルツマンの方程式によって与えられます：

$$
Qᵢᵣ = σ(T⁴ - Tₐ⁴),
$$

ここで $σ$ はステファン・ボルツマン定数、$T$ は海洋温度、$Tₐ$ は2mの空気温度です。

顕熱と潜熱フラックスは、[fairall2011](@citet) で説明されているブロックパラメータ化によって与えられます：

$$
Qₛ = ρₐcₚₐCₕS(T - Tₐ),
$$

および $Qₗ = ρₐLₑCₕS(q(T) - qₐ)$、ここで $ρₐ$ は空気の密度、$cₚₐ$ は空気の比熱、$Cₕ$ は熱伝達係数、$S$ は風速、$Lₑ$ は `latent_heat_vaporisation` によってパラメータ化された蒸発潜熱、$q(T)$ は水の飽和水蒸気圧であり、`vapour_pressure` によってパラメータ化されています。

熱伝達係数は `WindStress` と同じパラメータ化によって与えられます。たとえば、`LogarithmicNeutralWind` の場合、伝達係数は次のように与えられます：$C_h = \frac{\kappa}{\log{\frac{2}{z_0}}}\frac{\kappa}{\log{\frac{2}{z_{ot}}}}$、ここで $z_{ot}$ は次のように与えられるスカラー粗さパラメータです：$z_{ot} = \min\left(1.15\cdot10^{-4}, 5.5\cdot10^{-5}R_r^{-0.6}\right)$、ここで $R_r$ は次のように与えられる粗さレイノルズ数です：$R_r = \frac{u\star z_0}{\nu}$、ここで $\nu$ は空気の運動粘度です。

熱フラックスは次のように与えられます：

$$
F = \frac{Q}{\rho_oc_{po}},
$$

ここで $\rho_o$ と $c_{po}$ は水の密度と比熱です。

（注：私たちは、上部境界での負の熱フラックスが温度を上昇させるというOceananigansの慣習を保持します）。

# キーワード引数

  * `wind_stress`: 風応力モデル
  * `air_temperature`: 空気温度（°C）を `(x, y, t)` の署名を持つ関数または定数として
  * `latent_heat_vaporisation`: 蒸発の潜熱（J / kg）
  * `vapour_pressure`: 水の飽和水蒸気圧のパラメータ化
  * `water_specific_heat_capacity`: 水の比熱（J / K / kg）
  * `water_density`: 水の密度（kg / m³）
  * `air_specific_heat_capacit`: 空気の比熱（J / K / kg）
  * `air_density`: 空気の密度（kg / m³）
  * `air_water_mixing_ratio`: 空気中の水分量（kg / kg）
  * `stephan_boltzman_constant`: ステファン・ボルツマン定数（W / K⁴）

# 例

```jldoctest
julia> using Walrus

julia> using Oceananigans

julia> wind_stress = WindStress(; reference_wind_speed = 0., reference_wind_direction = 90.)
(::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) (generic function with 2 methods)

julia> surface_heat_exchange = SurfaceHeatExchange(; wind_stress)
(::SurfaceHeatExchange{WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}, Int64, Walrus.SurfaceHeatingModel.EmpiricalLatentHeatVaporisation{Float64}, Walrus.SurfaceHeatingModel.AugustRocheMagnusVapourPressure{Float64}, Float64, Walrus.SurfaceHeatingModel.EmpiricalDownwellingLongwave{Float64, Float64}}) (generic function with 1 method)

julia> boundary_conditions = (; T = FieldBoundaryConditions(top = FluxBoundaryCondition(surface_heat_exchange, field_dependencies = (:T, :u, :v))))
(T = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── top: FluxBoundaryCondition: ContinuousBoundaryFunction (::SurfaceHeatExchange{WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}, Int64, Walrus.SurfaceHeatingModel.EmpiricalLatentHeatVaporisation{Float64}, Walrus.SurfaceHeatingModel.AugustRocheMagnusVapourPressure{Float64}, Float64, Walrus.SurfaceHeatingModel.EmpiricalDownwellingLongwave{Float64, Float64}}) at (Nothing, Nothing, Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing),)

```
