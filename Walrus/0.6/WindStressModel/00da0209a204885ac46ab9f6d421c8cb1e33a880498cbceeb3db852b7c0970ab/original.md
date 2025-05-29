```
WindStress(; reference_wind_speed, 
             reference_wind_direction,
             drag_coefficient = LogarithmicNeutralWind(), 
             air_density = 1.225, 
             water_density = 1026.)
```

Returns a wind stress model where the stress is given by,

$$
\frac{\tau}{\rho_o} = \rho_aC_dSU_{x/y},
$$

where $\rho_o$ is the water density, $\rho_a$ is the air density, $C_d$ is the drag coefficient, $U_{x/y}$ are the x and y components of  relative wind speed, and $S=\sqrt{U_x^2+U_y^2}$.

$C_d$ is calculated from a parameterisation, by default this is a "log neutral" wind parameterisation with velocity roughness length parameterisaion like [smith1988](@citet).

In the default configuration this is the same as described in [fairall2011](@citet).

# Keyword Arguments

  * `reference_wind_speed` (required): a function returning the (10m neutral) wind speed in the form `reference_wind_speed(x, y, t)` or single value
  * `reference_wind_direction` (required): a function returning the (10m neutral) wind direction in the form `reference_wind_direction(x, y, t)` or single value
  * `drag_coefficient`: the drag coefficient parameterisation
  * `air_density`: air density in kg/m³
  * `water_density`: water density in kg/m³

# Example

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
