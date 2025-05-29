```
SolidHfusModel <: EoSModel

SolidHfus(components;
userlocations = String[],
verbose::Bool=false)
```

## Parameters

  * `Hfus`: Single Parameter (`Float64`) - Enthalpy of Fusion at 1 bar `[J/mol]`
  * `Tm`: Single Parameter (`Float64`) - Melting Temperature `[K]`
  * `CpSL`: Single Parameter (`Float64`) (optional) - Heat Capacity of the Solid-Liquid Phase Transition `[J/mol/K]`

## Description

Approximation of the excess chemical potential in the solid phase (`CpSL` is not necessary by default):

```
ln(xᵢγᵢ) = Hfusᵢ*T*(1/Tmᵢ-1/T)-CpSLᵢ/R̄*(Tmᵢ/T-1-log(Tmᵢ/T))
```
