```
Substance{N,VAP,D_G,D_L,F,H,CP_G,CP_L}(;kwargs...)
```

A simple container for the physical and thermal properties of substances.

`vapor_pressure`, `latent_heat`, `gas_heat_capacity`, and `liquid_heat_capacity` can be functions of temperature (in Kelvin) or constants.

`gas_density` and `liquid_density` can be functions of temperature (in Kelvin) and pressure (in Pascal) or constants.

# Arguments

  * `name<:Union{AbstractString,Symbol}`: the name of the substance
  * `molar_weight::Number`: the molar weight, kg/mol
  * `vapor_pressure<:Union{Number,Function,Nothing}=nothing`: the vapor pressure, Pa. If `nothing` then the Clausius-Clapeyron equation is used to derive a vapor pressure curve
  * `gas_density<:Union{Number,Function,Nothing}=nothing`: the gas density, kg/m³. If `nothing` the ideal gas law is used.
  * `liquid_density<:Union{Number,Function}`: the liquid density, kg/m³.
  * `reference_temp::Number=288.15`: the reference temperature for the given properties, K.
  * `reference_pressure::Number=101325`: the reference pressure for the given properties, Pa.
  * `k::Number=1.4`: the isentropic expansion factor, cp/cv, unitless.
  * `boiling_temp<:Union{Number,Function}::Number`: the normal boiling temperature, K.
  * `latent_heat<:Union{Number,Function}`: the latent heat of vaporization, J/kg.
  * `gas_heat_capacity<:Union{Number,Function}`: the gas heat capacity, J/kg/K.
  * `liquid_heat_capacity<:Union{Number,Function}`: the liquid heat capacity, J/kg/K.
