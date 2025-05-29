```
WindStressBoundaryConditions(; reference_wind_speed, 
                               reference_wind_direction,
                               drag_coefficient = LogarithmicNeutralWind(), 
                               air_density = 1.225, 
                               water_density = 1026.)
```

`WindStress` 境界条件を設定するための便利なコンストラクタです。

# キーワード引数

  * `reference_wind_speed` (必須): `reference_wind_speed(x, y, t)` の形式で (10m 中立) 風速を返す関数または単一の値
  * `reference_wind_direction` (必須): `reference_wind_direction(x, y, t)` の形式で (10m 中立) 風向を返す関数または単一の値
  * `drag_coefficient`: 抵抗係数のパラメータ化
  * `air_density`: 空気密度 (kg/m³)
  * `water_density`: 水密度 (kg/m³)

# 例

```jldoctest
julia> using Walrus: WindStressBoundaryConditions

julia> using Oceananigans

julia> wind_stress_boundary_conditions = WindStressBoundaryConditions(; reference_wind_speed = 0.1, reference_wind_direction = 90.)
(u = FluxBoundaryCondition: DiscreteBoundaryFunction (::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) with parameters Val{:x}, v = FluxBoundaryCondition: DiscreteBoundaryFunction (::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) with parameters Val{:y})

julia> boundary_conditions = (u = FieldBoundaryConditions(top = wind_stress_boundary_conditions.u),
                              v = FieldBoundaryConditions(top = wind_stress_boundary_conditions.v))
(u = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── top: FluxBoundaryCondition: DiscreteBoundaryFunction (::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) with parameters Val{:x}
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing), v = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── top: FluxBoundaryCondition: DiscreteBoundaryFunction (::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) with parameters Val{:y}
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing))

```
