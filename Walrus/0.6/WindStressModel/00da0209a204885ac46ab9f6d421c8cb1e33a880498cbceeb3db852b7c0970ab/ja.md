```
WindStress(; reference_wind_speed, 
             reference_wind_direction,
             drag_coefficient = LogarithmicNeutralWind(), 
             air_density = 1.225, 
             water_density = 1026.)
```

風応力モデルを返し、応力は次のように与えられます。

$$
\frac{\tau}{\rho_o} = \rho_aC_dSU_{x/y},
$$

ここで、$\rho_o$は水の密度、$\rho_a$は空気の密度、$C_d$は抗力係数、$U_{x/y}$は相対風速のxおよびy成分、$S=\sqrt{U_x^2+U_y^2}$です。

$$
C_d
$$

はパラメータ化から計算され、デフォルトでは「対数中立」風のパラメータ化で、速度粗さ長さのパラメータ化が含まれています [smith1988](@citet)。

デフォルトの構成では、これは [fairall2011](@citet) に記載されているものと同じです。

# キーワード引数

  * `reference_wind_speed` (必須): `reference_wind_speed(x, y, t)` の形式で (10m 中立) 風速を返す関数または単一の値
  * `reference_wind_direction` (必須): `reference_wind_direction(x, y, t)` の形式で (10m 中立) 風向を返す関数または単一の値
  * `drag_coefficient`: 抗力係数のパラメータ化
  * `air_density`: 空気の密度 (kg/m³)
  * `water_density`: 水の密度 (kg/m³)

# 例

```jldoctest
julia> using Walrus: WindStress

julia> using Oceananigans

julia> reference_wind_speed = 0.1
0.1

julia> reference_wind_direction = 0.
0.0

julia> wind_stress = WindStress(; reference_wind_speed, reference_wind_direction)
(::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) (generic function with 2 methods)

julia> boundary_conditions = (u = FieldBoundaryConditions(top = FluxBoundaryCondition(wind_stress, parameters = Val(:x))),
                              v = FieldBoundaryConditions(top = FluxBoundaryCondition(wind_stress, parameters = Val(:y))))
(u = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── top: FluxBoundaryCondition: ContinuousBoundaryFunction (::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) at (Nothing, Nothing, Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing), v = Oceananigans.FieldBoundaryConditions, with boundary conditions
├── west: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── east: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── south: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── north: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── bottom: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing)
├── top: FluxBoundaryCondition: ContinuousBoundaryFunction (::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) at (Nothing, Nothing, Nothing)
└── immersed: DefaultBoundaryCondition (FluxBoundaryCondition: Nothing))

```
