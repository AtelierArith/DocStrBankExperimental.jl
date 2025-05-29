```
SeawaterBuoyancy([FT = Float64;]
                 gravitational_acceleration = g_Earth,
                 equation_of_state = LinearEquationOfState(FT),
                 constant_temperature = nothing,
                 constant_salinity = nothing)
```

Return parameters for a temperature- and salt-stratified seawater buoyancy model with a `gravitational_acceleration` constant (typically called $g$), and an `equation_of_state` that related temperature and salinity (or conservative temperature and absolute salinity) to density anomalies and buoyancy.

Setting `constant_temperature` to something that is not `nothing` indicates that buoyancy depends only on salinity. For a nonlinear equation of state, the value provided `constant_temperature` is used as the temperature of the system. Vice versa, setting `constant_salinity` indicates that buoyancy depends only on temperature.

For a linear equation of state, the values of `constant_temperature` or `constant_salinity` are irrelevant.

# Examples

The "TEOS10" equation of state, see https://www.teos-10.org

```jldoctest seawaterbuoyancy
julia> using SeawaterPolynomials.TEOS10: TEOS10EquationOfState

julia> teos10 = TEOS10EquationOfState()
BoussinesqEquationOfState{Float64}:
├── seawater_polynomial: TEOS10SeawaterPolynomial{Float64}
└── reference_density: 1020.0
```

Buoyancy that depends on both temperature and salinity

```jldoctest seawaterbuoyancy
julia> using Oceananigans

julia> buoyancy = SeawaterBuoyancy(equation_of_state=teos10)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
└── equation_of_state: BoussinesqEquationOfState{Float64}
```

Buoyancy that depends only on salinity with temperature held at 20 degrees Celsius

```jldoctest seawaterbuoyancy
julia> salinity_dependent_buoyancy = SeawaterBuoyancy(equation_of_state=teos10, constant_temperature=20)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
├── constant_temperature: 20.0
└── equation_of_state: BoussinesqEquationOfState{Float64}
```

Buoyancy that depends only on temperature with salinity held at 35 psu

```jldoctest seawaterbuoyancy
julia> temperature_dependent_buoyancy = SeawaterBuoyancy(equation_of_state=teos10, constant_salinity=35)
SeawaterBuoyancy{Float64}:
├── gravitational_acceleration: 9.80665
├── constant_salinity: 35.0
└── equation_of_state: BoussinesqEquationOfState{Float64}
```
