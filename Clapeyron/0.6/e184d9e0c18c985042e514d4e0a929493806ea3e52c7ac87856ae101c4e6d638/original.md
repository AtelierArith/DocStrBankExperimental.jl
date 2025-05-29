```
PPR78Rule <: PPR78RuleModel

PPR78Rule(components;
userlocations = String[],
group_userlocations = String[]
verbose::Bool=false)
```

## Input Parameters

  * `A`: Pair Parameter (`Float64`) - Fitted Parameter `[K]`
  * `B`: Pair Parameter (`Float64`) - Fitted Parameter `[K]`

## Description

PPR78 Mixing Rule, Uses E-PPR78 Group params. Default for [`EPPR78`](@ref) EoS.

```
aᵢⱼ = √(aᵢaⱼ)
bᵢⱼ = (bᵢ +bⱼ)/2
b̄ = ∑bᵢⱼxᵢxⱼ
c̄ = ∑cᵢxᵢ
ā = b̄(∑[xᵢaᵢαᵢ/(bᵢᵢ)] - ∑xᵢxⱼbᵢbⱼEᵢⱼ/2b̄)
Eᵢⱼ = ∑(z̄ᵢₖ - z̄ⱼₖ)(z̄ᵢₗ - z̄ⱼₗ) × Aₖₗ × (298.15/T)^(Aₖₗ/Bₖₗ - 1)
```

## References

1. Jaubert, J.-N., Privat, R., & Mutelet, F. (2010). Predicting the phase equilibria of synthetic petroleum fluids with the PPR78 approach. AIChE Journal. American Institute of Chemical Engineers, 56(12), 3225–3235. [doi:10.1002/aic.12232](https://doi.org/10.1002/aic.12232)
2. Jaubert, J.-N., Qian, J.-W., Lasala, S., & Privat, R. (2022). The impressive impact of including enthalpy and heat capacity of mixing data when parameterising equations of state. Application to the development of the E-PPR78 (Enhanced-Predictive-Peng-Robinson-78) model. Fluid Phase Equilibria, (113456), 113456. [doi:10.1016/j.fluid.2022.113456](https://doi.org/10.1016/j.fluid.2022.113456)
