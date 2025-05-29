GEDeparture <: MultiFluidDepartureModel     GEDeparture(components;     activity = UNIFAC,     userlocations = String[],     verbose = false)

## Input parameters

none

  * `k1`: Pair Parameter (`Float64`) - binary, T-dependent interaction parameter `[K^-1]`

## Model parameters

  * `vref`: Single Parameter (`Float64`, calculated) - Reference pure molar volume `[m3/mol]`

## Input models

  * `activity`: activity model

## Description

Departure that uses the residual excess gibbs energy from an activity model:

```
aᵣ = ∑xᵢaᵣᵢ(δ,τ) + Δa
Δa = gᴱᵣ/RT - log(1+bρ)/log(1+bρref) * ∑xᵢ(aᵣᵢ(δref,τ) - aᵣᵢ(δrefᵢ,τᵢ))
τᵢ = Tcᵢ/T
δref = ρref/ρr
δrefᵢ = ρrefᵢ/ρcᵢ
b = 1/1.17ρref
```

## References

1. Jäger, A., Breitkopf, C., & Richter, M. (2021). The representation of cross second virial coefficients by multifluid mixture models and other equations of state. Industrial & Engineering Chemistry Research, 60(25), 9286–9295. [doi:10.1021/acs.iecr.1c01186](https://doi.org/10.1021/acs.iecr.1c01186)
