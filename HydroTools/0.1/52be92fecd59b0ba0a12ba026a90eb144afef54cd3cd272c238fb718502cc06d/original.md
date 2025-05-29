```
ET0_eq(Rn::T, Tair::T, Pa::T=atm, args...)
```

Equilibrium evaporation, `ET0_eq = Δ / (Δ + γ) * Rn`

# Arguments

  * `Rn`   : net radiation (W m-2)
  * `Tair` : 2m air temperature (degC)
  * `VPD`  : vapor pressure deficit (kPa)
  * `Pa`   : surface air pressure (kPa)

# Returns

  * `λ` : latent heat of vaporization (MJ kg-1)
  * `Δ`  : slope of the saturation vapor pressure curve (kPa degC-1)
  * `γ`  : psychrometric constant (kPa degC-1)
  * `Eeq`    : equilibrium evaporation rate (mm day-1)

# Optional keyword arguments

  * `args...` : additional arguments (not used in this function)

# Examples

```julia
julia> ET0_eq(200.0, 20.0)
(2.4536, 0.14474018811241365, 0.06725596686893338, 4.808405926729265)
```
