```
latent_heat_liq_ice(param_set, q::PhasePartition{FT})
```

Effective latent heat of condensate (weighted sum of liquid and ice), with specific latent heat evaluated at reference temperature `T_0` given

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.
