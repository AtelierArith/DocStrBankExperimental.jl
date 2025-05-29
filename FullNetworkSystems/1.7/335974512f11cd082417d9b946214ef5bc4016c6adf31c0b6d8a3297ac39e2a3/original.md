```julia
struct GeneratorStatusRT <: FullNetworkSystems.GeneratorStatus
```

Generator status time series data needed for the real-time formulation.

Fields:

  * `commitment::AxisKeys.KeyedArray{Bool, 2}`: Generator commitment status indicated by a `Bool`
  * `regulation_commitment::AxisKeys.KeyedArray{Bool, 2}`: Generator regulation commitment status indicated by a `Bool`
