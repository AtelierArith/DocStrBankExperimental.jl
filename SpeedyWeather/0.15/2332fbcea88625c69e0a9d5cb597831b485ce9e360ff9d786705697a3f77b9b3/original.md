Parameters for computing saturation vapour pressure of water using the Clausis-Clapeyron equation,

```
e(T) = e₀ * exp( -Lᵥ/Rᵥ * (1/T - 1/T₀)),
```

where T is in Kelvin, Lᵥ the the latent heat of condensation and Rᵥ the gas constant of water vapour

  * `e₀::AbstractFloat`: Saturation water vapour pressure at 0°C [Pa]
  * `T₀::AbstractFloat`: 0°C in Kelvin
  * `Lᵥ::AbstractFloat`: Latent heat of condensation/vaporization of water [J/kg]
  * `cₚ::AbstractFloat`: Specific heat at constant pressure [J/K/kg]
  * `R_vapour::AbstractFloat`: Gas constant of water vapour [J/kg/K]
  * `R_dry::AbstractFloat`: Gas constant of dry air [J/kg/K]
  * `Lᵥ_Rᵥ::AbstractFloat`: Latent heat of condensation divided by gas constant of water vapour [K]
  * `T₀⁻¹::AbstractFloat`: Inverse of T₀, one over 0°C in Kelvin
  * `mol_ratio::AbstractFloat`: Ratio of molecular masses [1] of water vapour over dry air (=R*dry/R*vapour).
