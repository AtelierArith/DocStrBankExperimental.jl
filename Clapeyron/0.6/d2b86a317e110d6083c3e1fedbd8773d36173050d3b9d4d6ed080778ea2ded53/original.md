```
SolidKsModel <: EoSModel

SolidKs(components;
userlocations = String[],
verbose::Bool=false)
```

## Parameters

  * `Hfus`: Single Parameter (`Float64`) - Enthalpy of Fusion at 1 bar `[J/mol]`
  * `Tm`: Single Parameter (`Float64`) - Melting Temperature `[K]`
  * `CpSL`: Single Parameter (`Float64`) - Heat Capacity of the Solid-Liquid Phase Transition `[J/mol/K]`

## Description

Approximation of the excess chemical potential in the solid phase, using enthalpies and gibbs energies of formation:

```
ln(xᵢγᵢ) = -Gformᵢ*T/Trefᵢ - Hformᵢ*(1 - T/Trefᵢ)
```
