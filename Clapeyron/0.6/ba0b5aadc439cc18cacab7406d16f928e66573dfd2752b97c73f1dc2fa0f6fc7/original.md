```
SuperAncSaturation <: SaturationMethod
SuperAncSaturation()
```

Saturation method for `saturation_pressure`. it uses Chebyshev expansions constructed with extended precision arithmetic to obtain the saturation curves of supported EoS within `Float64` precision. models supported are:

  * [vdW](@ref) models and variants
  * [RK](@ref) models and variants
  * [PR](@ref) models and variants
  * [PCSAFT](@ref) models and some variants (via `EoSSuperancillaries.jl` package extension)

## References

1. Bell, I. H., & Deiters, U. K. (2021). Superancillary equations for cubic equations of state. Industrial & Engineering Chemistry Research, 60(27), 9983–9991. doi:10.1021/acs.iecr.1c00847
