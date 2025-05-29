```
DIPPR101Sat <: SaturationModel

DIPPR101Sat(components;
userlocations = String[],
verbose::Bool=false)
```

## Input Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `A`: Single Parameter (`Float64`)
  * `B`: Single Parameter (`Float64`)
  * `C`: Single Parameter (`Float64`)
  * `D`: Single Parameter (`Float64`)
  * `E`: Single Parameter (`Float64`)
  * `Tmin`: Single Parameter (`Float64`)  - mininum Temperature range `[K]`
  * `Tmax`: Single Parameter (`Float64`)  - maximum Temperature range `[K]`

## Model Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `A`: Single Parameter (`Float64`)
  * `B`: Single Parameter (`Float64`)
  * `C`: Single Parameter (`Float64`)
  * `D`: Single Parameter (`Float64`)
  * `E`: Single Parameter (`Float64`)
  * `Tmin`: Single Parameter (`Float64`)  - mininum Temperature range `[K]`
  * `Tmax`: Single Parameter (`Float64`)  - maximum Temperature range `[K]`

## Description

DIPPR 101 Equation for saturation pressure:

```
psat(T) = exp(A + B/T + C•log(T) + D•T^E)
```

## References

1. Design Institute for Physical Properties, 1996. DIPPR Project 801 DIPPR/AIChE
