```
EPPR78(components_or_groups;
idealmodel = BasicIdeal,
alpha = PR78Alpha,
mixing = PPR78Rule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

Enhanced Predictive Peng Robinson equation of state. it uses the following models:

  * Translation Model: [`NoTranslation`](@ref)
  * Alpha Model: [`PR78Alpha`](@ref)
  * Mixing Rule Model: [`PPR78Rule`](@ref)

## References

1. Jaubert, J.-N., Privat, R., & Mutelet, F. (2010). Predicting the phase equilibria of synthetic petroleum fluids with the PPR78 approach. AIChE Journal. American Institute of Chemical Engineers, 56(12), 3225–3235. [doi:10.1002/aic.12232](https://doi.org/10.1002/aic.12232)
2. Jaubert, J.-N., Qian, J.-W., Lasala, S., & Privat, R. (2022). The impressive impact of including enthalpy and heat capacity of mixing data when parameterising equations of state. Application to the development of the E-PPR78 (Enhanced-Predictive-Peng-Robinson-78) model. Fluid Phase Equilibria, (113456), 113456. [doi:10.1016/j.fluid.2022.113456](https://doi.org/10.1016/j.fluid.2022.113456)
