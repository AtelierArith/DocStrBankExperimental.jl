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

Specifies surface heat exhange in the form:

$$
Q = Qᵢᵣ + Qₛ + Qₗ,
$$

where $Qᵢᵣ$ is the heat flux due to long wave (infra red) radiation, $Qₛ$ is the sensible heat flux, and $Qₗ$ is the latent heat flux. Notably the short wave radiation flux is neglegted here as it is assumed to penatrate far enough into the  water that it is treated separately by `HomogeneousBodyHeating` (we therefore are also assuming that the short wave penitration is suitably short that it is neglected).

The short wave term is given by the Stephan-Boltzman equation so:

$$
Qᵢᵣ = σ(T⁴ - Tₐ⁴),
$$

where $σ$ is the Stephan-Boltzman constant, $T$ is the ocean temperature, and $Tₐ$ is the 2m air temperature. 

The sensible and latent heat flux's are given by the bluk parameterisations described in  [fairall2011](@citet) and are given by:

$$
Qₛ = ρₐcₚₐCₕS(T - Tₐ),
$$

and $Qₗ = ρₐLₑCₕS(q(T) - qₐ)$,  where $ρₐ$ is the density of the air, $cₚₐ$ is the specific heat capacity of air,  $Cₕ$ is the heat transfer coefficient, $S$ is the wind speed, $Lₑ$ is the latent heat of vaporizaion parameterised by `latent_heat_vaporisation`, $q(T)$ is the  saturation vapour pressure of water and is parameterised by `vapour_pressure`.

The heat transfer coefficients are given by the same parameterisation as the `WindStress`. For example for the `LogarithmicNeutralWind` the transfer coefficient is given as: $C_h = \frac{\kappa}{\log{\frac{2}{z_0}}}\frac{\kappa}{\log{\frac{2}{z_{ot}}}}$, where $z_{ot}$ is the sclar roughness parameter given by: $z_{ot} = \min\left(1.15\cdot10^{-4}, 5.5\cdot10^{-5}R_r^{-0.6}\right)$, where $R_r$ is the roughness reynolds number given as $R_r = \frac{u\star z_0}{\nu}$ where $\nu$ is the kinematic viscosity of air.

The heat flux is then given by:

$$
F = \frac{Q}{\rho_oc_{po}},
$$

where $\rho_o$ and $c_{po}$ are the density and specific heat capacity of water.

(Note: we will retain the Oceananigans convention that negative heat flux   at a top boundary increases temeprature).

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
