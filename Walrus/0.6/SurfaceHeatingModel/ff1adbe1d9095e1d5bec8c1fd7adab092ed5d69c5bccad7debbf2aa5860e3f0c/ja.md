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
                      ocean_emissivity = 0.97) #
```

便利なコンストラクタで、境界条件として `SurfaceHeatExchange` を返します

# キーワード引数

  * `wind_stress`: 風応力モデル
  * `air_temperature`: 空気温度（°C）で、シグネチャ `(x, y, t)` の関数または定数
  * `latent_heat_vaporisation`: 蒸発潜熱（J / kg）
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

julia> wind_stress = WindStress(; reference_wind_speed = 0., reference_wind_direction = 90.)
(::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) (generic function with 2 methods)

julia> surface_heat_exchange = SurfaceHeatExchangeBoundaryCondition(; wind_stress)
FluxBoundaryCondition: DiscreteBoundaryFunction with (::SurfaceHeatExchange{WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}, Int64, Walrus.SurfaceHeatingModel.EmpiricalLatentHeatVaporisation{Float64}, Walrus.SurfaceHeatingModel.AugustRocheMagnusVapourPressure{Float64}, Float64, Walrus.SurfaceHeatingModel.EmpiricalDownwellingLongwave{Float64, Float64}})
```
