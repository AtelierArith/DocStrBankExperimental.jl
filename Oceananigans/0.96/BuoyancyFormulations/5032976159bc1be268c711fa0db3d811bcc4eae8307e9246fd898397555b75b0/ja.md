```
SeawaterBuoyancy([FT = Float64;]
                 gravitational_acceleration = g_Earth,
                 equation_of_state = LinearEquationOfState(FT),
                 constant_temperature = nothing,
                 constant_salinity = nothing)
```

温度および塩分層化された海水浮力モデルのパラメータを返します。`gravitational_acceleration` 定数（通常 $g$ と呼ばれる）と、温度と塩分（または保守的温度と絶対塩分）を密度異常と浮力に関連付ける `equation_of_state` を持ちます。

`constant_temperature` を `nothing` でない何かに設定すると、浮力は塩分のみに依存することを示します。非線形状態方程式の場合、提供された `constant_temperature` の値はシステムの温度として使用されます。逆に、`constant_salinity` を設定すると、浮力は温度のみに依存することを示します。

線形状態方程式の場合、`constant_temperature` または `constant_salinity` の値は無関係です。

# 例

"TEOS10" 状態方程式、詳細は https://www.teos-10.org を参照

```jldoctest seawaterbuoyancy
julia> using SeawaterPolynomials.TEOS10: TEOS10EquationOfState

julia> teos10 = TEOS10EquationOfState()
BoussinesqEquationOfState{Float64}:
├── seawater_polynomial: TEOS10SeawaterPolynomial{Float64}
└── reference_density: 1020.0
```

温度と塩分の両方に依存する浮力

```jldoctest seawaterbuoyancy
julia> using Oceananigans

julia> buoyancy = SeawaterBuoyancy(equation_of_state=teos10)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
└── equation_of_state: BoussinesqEquationOfState{Float64}
```

温度を20度セルシウスに保った塩分のみに依存する浮力

```jldoctest seawaterbuoyancy
julia> salinity_dependent_buoyancy = SeawaterBuoyancy(equation_of_state=teos10, constant_temperature=20)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
├── constant_temperature: 20.0
└── equation_of_state: BoussinesqEquationOfState{Float64}
```

塩分を35 psuに保った温度のみに依存する浮力

```jldoctest seawaterbuoyancy
julia> temperature_dependent_buoyancy = SeawaterBuoyancy(equation_of_state=teos10, constant_salinity=35)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
├── constant_salinity: 35.0
└── equation_of_state: BoussinesqEquationOfState{Float64}
```
