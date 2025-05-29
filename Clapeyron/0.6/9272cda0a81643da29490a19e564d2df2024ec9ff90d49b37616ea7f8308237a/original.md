```
UMRPR(components;
idealmodel = BasicIdeal,
userlocations = String[],
group_userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

Universal Mixing Rule Peng Robinson equation of state. it uses the following models:

  * Translation Model: [`MTTranslation`](@ref)
  * Alpha Model: [`MTAlpha`](@ref)
  * Mixing Rule Model: [`UMRRule`](@ref) with [`UNIFAC`](@ref) activity

## References

1. Voutsas, E., Magoulas, K., & Tassios, D. (2004). Universal mixing rule for cubic equations of state applicable to symmetric and asymmetric systems: Results with the Peng−Robinson equation of state. Industrial & Engineering Chemistry Research, 43(19), 6238–6246. [doi:10.1021/ie049580p](https://doi.org/10.1021/ie049580p)
