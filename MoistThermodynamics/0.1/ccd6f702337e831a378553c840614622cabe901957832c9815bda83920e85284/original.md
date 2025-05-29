```
(R_m, cp_m, cv_m, γ_m) = gas_constants([q::PhasePartition])
```

Wrapper to compute all gas constants at once, where optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.

The function returns a tuple of

  * `R_m` [`gas_constant_air`](@ref)
  * `cp_m` [`cp_m`](@ref)
  * `cv_m` [`cv_m`](@ref)
  * `γ_m = cp_m/cv_m`
