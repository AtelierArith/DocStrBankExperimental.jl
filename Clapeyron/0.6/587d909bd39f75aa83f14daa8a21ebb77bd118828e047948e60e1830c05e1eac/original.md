```
Clausius(components;
idealmodel = BasicIdeal,
alpha = NoAlpha,
mixing = vdW1fRule,
activity = nothing,
translation = ClausiusTranslation,
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
  * `Vc`: Single Parameter (`Float64`) - Molar Volume `[m^3/mol]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `k`: Pair Parameter (`Float64`) (optional)
  * `l`: Pair Parameter (`Float64`) (optional)

## Model Parameters

  * `Tc`: Single Parameter (`Float64`) - Critical Temperature `[K]`
  * `Pc`: Single Parameter (`Float64`) - Critical Pressure `[Pa]`
  * `Vc`: Single Parameter (`Float64`) - Molar Volume `[m^3/mol]`
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `a`: Pair Parameter (`Float64`)
  * `b`: Pair Parameter (`Float64`)

## Description

Clausius Equation of state.

```
P = RT/(v-b) + a•α(T)/((v - Δ₀b)^2)

aᵢᵢ =27/64 * (RTcᵢ)²/Pcᵢ
bᵢᵢ = Vcᵢ - 1/4 * RTcᵢ/Pcᵢ
cᵢ = 3/8 * RTcᵢ/Pcᵢ - Vcᵢ

Δ₀ = ∑cᵢxᵢ/∑bᵢxᵢ

```

## References

1. Clausius, R. (1880). Ueber das Verhalten der Kohlensäure in Bezug auf Druck, Volumen und Temperatur. Annalen der Physik, 245(3), 337–357. [doi:10.1002/andp.18802450302](https://doi.org/10.1002/andp.18802450302)
