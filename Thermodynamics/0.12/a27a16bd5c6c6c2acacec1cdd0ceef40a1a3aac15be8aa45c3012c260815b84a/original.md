```
(R_m, cp_m, cv_m, γ_m) = gas_constants(param_set, q::PhasePartition)
```

Wrapper to compute all gas constants at once, where optionally,

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `q` [`PhasePartition`](@ref).

The function returns a tuple of

  * `R_m` [`gas_constant_air`](@ref)
  * `cp_m` [`cp_m`](@ref)
  * `cv_m` [`cv_m`](@ref)
  * `γ_m = cp_m/cv_m`
