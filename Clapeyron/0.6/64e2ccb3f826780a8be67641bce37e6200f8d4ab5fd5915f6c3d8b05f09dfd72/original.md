```
QuadraticDeparture <: MultiFluidDepartureModel
QuadraticDeparture(components;
userlocations = String[],
verbose = false)
```

## Input parameters

  * `k0`: Pair Parameter (`Float64`) - binary interaction parameter  (no units)
  * `k1`: Pair Parameter (`Float64`) - binary, T-dependent interaction parameter `[K^-1]`

## Description

Departure that uses a quadratic mixing rule:

```
aᵣ = ∑xᵢxⱼaᵣᵢⱼ
aᵣᵢⱼ = 0.5*(aᵣᵢ + aᵣⱼ)*(1 - (k₀ + k₁T))
```

## References

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
