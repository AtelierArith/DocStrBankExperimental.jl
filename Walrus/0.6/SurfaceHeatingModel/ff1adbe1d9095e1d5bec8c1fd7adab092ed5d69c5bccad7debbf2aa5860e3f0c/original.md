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

A convenience constructor returning `SurfaceHeatExchange` as a boundary condition

# Keyword Arguments

  * `wind_stress`: wind stress model
  * `air_temperature`: the air temperature in °C as a function with signature `(x, y, t)` or a constant
  * `latent_heat_vaporisation`: latent heat of vaporisation in J / kg
  * `vapour_pressure`: parameterisation for saturation vapour pressure in water
  * `water_specific_heat_capacity`: the specific heat capacity of water in J / K / kg
  * `water_density`: water density in kg / m³
  * `air_specific_heat_capacit`: the specific heat capacity of air in J / K / kg
  * `air_density`: air density in kg / m³
  * `air_water_mixing_ratio`: water content of air in kg / kg
  * `stephan_boltzman_constant`: the Stephan-Boltzman constant in W / K⁴

# Example

```jldoctest
julia> using Walrus

julia> wind_stress = WindStress(; reference_wind_speed = 0., reference_wind_direction = 90.)
(::WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}) (generic function with 2 methods)

julia> surface_heat_exchange = SurfaceHeatExchangeBoundaryCondition(; wind_stress)
FluxBoundaryCondition: DiscreteBoundaryFunction with (::SurfaceHeatExchange{WindStress{Float64, Float64, LogarithmicNeutralWind{Float64, Nothing}, Float64}, Int64, Walrus.SurfaceHeatingModel.EmpiricalLatentHeatVaporisation{Float64}, Walrus.SurfaceHeatingModel.AugustRocheMagnusVapourPressure{Float64}, Float64, Walrus.SurfaceHeatingModel.EmpiricalDownwellingLongwave{Float64, Float64}})

```
