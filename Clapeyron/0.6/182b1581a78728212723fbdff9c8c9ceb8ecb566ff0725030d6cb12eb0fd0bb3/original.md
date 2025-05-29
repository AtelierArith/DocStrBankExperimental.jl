```
cPR(components::Vector{String};
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
alpha_userlocations = String[],
mixing_userlocations = String[],
activity_userlocations = String[],
translation_userlocations = String[],
reference_state = nothing,
verbose = false)
```

consistent Peng Robinson equation of state. it uses the following models:

  * Translation Model: [`NoTranslation`](@ref)
  * Alpha Model: [`TwuAlpha`](@ref)
  * Mixing Rule Model: [`vdW1fRule`](@ref)

## References

1. Bell, I. H., Satyro, M., & Lemmon, E. W. (2018). Consistent twu parameters for more than 2500 pure fluids from critically evaluated experimental data. Journal of Chemical and Engineering Data, 63(7), 2402–2409. [doi:10.1021/acs.jced.7b00967](https://doi.org/10.1021/acs.jced.7b00967)
