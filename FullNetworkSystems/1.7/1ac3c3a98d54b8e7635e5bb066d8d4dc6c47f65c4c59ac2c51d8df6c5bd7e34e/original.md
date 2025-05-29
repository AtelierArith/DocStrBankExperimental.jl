```julia
struct GeneratorStatusDA <: FullNetworkSystems.GeneratorStatus
```

Generator status time series data needed for the day-ahead formulation.

Fields:

  * `hours_at_status::AxisKeys.KeyedArray{Float64, 1}`: Hours each generator has been at its current commitment status at the start of the day
  * `availability::AxisKeys.KeyedArray{Bool, 2}`: Flag indicating if the generator is available to be committed in each hour
  * `must_run::AxisKeys.KeyedArray{Bool, 2}`: Flag indicating if the generator must be committed in each hour
