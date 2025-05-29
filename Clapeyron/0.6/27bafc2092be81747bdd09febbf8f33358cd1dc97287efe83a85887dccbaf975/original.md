```
Berthelot(components;
idealmodel = BasicIdeal,
alpha = ClausiusAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = NoTranslation,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `Vc`: Single Parameter (`Float64`) - Molar Volume `[m^3/mol]`
  * `k`: Pair Parameter (`Float64`) (optional)

## Model Parameters

  * `a`: Pair Parameter (`Float64`)
  * `b`: Pair Parameter (`Float64`)
  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Vc`: Single Parameter (`Float64`) - Molar Volume `[m^3/mol]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`

## Input models

  * `idealmodel`: Ideal Model
  * `alpha`: Alpha model
  * `mixing`: Mixing model
  * `activity`: Activity Model, used in the creation of the mixing model.
  * `translation`: Translation Model

## Description

Berthelot Equation of state. it uses the Volume-Pressure Based mixing rules, that is:

```
a = 8*Pc*Vc^2
b = Vc/3
R = (8/3)*Pc*Vc/Tc
P = RT/(V-Nb) + a•α(T)/V²
α(T) = Tc/T
```

## References

1. Berthelot, D. (1899). Sur une méthode purement physique pour la détermination des poids moléculaires des gaz et des poids atomiques de leurs éléments. Journal de Physique Théorique et Appliquée, 8(1), 263–274. [doi:10.1051/jphystap:018990080026300](https://doi.org/10.1051/jphystap:018990080026300)
