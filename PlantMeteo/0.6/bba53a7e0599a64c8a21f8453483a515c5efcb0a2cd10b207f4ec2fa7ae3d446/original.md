Atmosphere structure to hold all values related to the meteorology / atmosphere.

# Arguments

  * `date<:AbstractDateTime = Dates.now()`: the date of the record.
  * `duration<:Period = Dates.Second(1.0)`: the duration of the time-step in Dates.Period.
  * `T` (°C): air temperature
  * `Wind` (m s-1): wind speed
  * `Rh` (0-1): relative humidity (can be computed using `rh_from_vpd`)
  * `P = DEFAULTS.P` (kPa): air pressure. The default value is at 1 atm, *i.e.* the mean sea-level

atmospheric pressure on Earth.

  * `Precipitations = DEFAULTS.Precipitations` (mm): precipitations from atmosphere (*i.e.* rain, snow, hail, etc.)
  * `Cₐ = DEFAULTS.Cₐ` (ppm): air CO₂ concentration
  * `check = true`: whether to check the validity of the input values.
  * `e = vapor_pressure(T,Rh)` (kPa): vapor pressure
  * `eₛ = e_sat(T)` (kPa): saturated vapor pressure
  * `VPD = eₛ - e` (kPa): vapor pressure deficit
  * `ρ = air_density(T, P, constants.Rd, constants.K₀)` (kg m-3): air density
  * `λ = latent_heat_vaporization(T, constants.λ₀)` (J kg-1): latent heat of vaporization
  * `γ = psychrometer_constant(P, λ, constants.Cₚ, constants.ε)` (kPa K−1): psychrometer "constant"
  * `ε = atmosphere_emissivity(T,e,constants.K₀)` (0-1): atmosphere emissivity
  * `Δ = e_sat_slope(meteo.T)` (0-1): slope of the saturation vapor pressure at air temperature
  * `clearness::A = Inf` (0-1): Sky clearness
  * `Ri_SW_f::A = Inf` (W m-2): Incoming short wave radiation flux
  * `Ri_PAR_f::A = Inf` (W m-2): Incoming PAR flux
  * `Ri_NIR_f::A = Inf` (W m-2): Incoming NIR flux
  * `Ri_TIR_f::A = Inf` (W m-2): Incoming TIR flux
  * `Ri_custom_f::A = Inf` (W m-2): Incoming radiation flux for a custom waveband

# Notes

The structure can be built using only `T`, `Rh`, `Wind` and `P`. All other variables are optional and either let at their default value or automatically computed using the functions given in `Arguments`.

# Examples

```julia
Atmosphere(T = 20.0, Wind = 1.0, P = 101.3, Rh = 0.65)
```
