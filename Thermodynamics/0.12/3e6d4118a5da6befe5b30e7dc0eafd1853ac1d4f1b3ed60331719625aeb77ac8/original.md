```
relative_humidity(param_set, T, p, phase_type, q::PhasePartition)
```

The relative humidity (clipped between 0 and 1), given

  * `param_set` an `AbstractParameterSet`, see the [`Thermodynamics`](@ref) for more details
  * `p` pressure
  * `phase_type` a thermodynamic state type

and, optionally,

  * `q` [`PhasePartition`](@ref). Without this argument, the results are for dry air.

```

```
