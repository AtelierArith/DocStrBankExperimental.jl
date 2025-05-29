```
CritExtrapolationSaturation <: SaturationMethod
CritExtrapolationSaturation(;crit = nothing)
```

Saturation method that extrapolates the liquid and vapor volumes from the critical point. the extrapolation is defined as:

```
ρₓ = ρc ± sqrt(6* Tc * (Tc - T)/Tc * ∂²p∂ρ∂T / ∂³p∂ρ³)
```

This method is specially useful at calculating the liquid and vapor volumes when T > 0.999Tc.

## References

1. Bell, I. H., & Deiters, U. K. (2023). Superancillary equations for nonpolar pure fluids modeled with the PC-SAFT equation of state. Industrial & Engineering Chemistry Research. [doi:10.1021/acs.iecr.2c02916](https://doi.org/10.1021/acs.iecr.2c02916)
