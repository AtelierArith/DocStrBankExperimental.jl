```
mutable struct Scenarios <: Forecast
    name::String
    resolution::Dates.Period
    scenario_count::Int64
    data::SortedDict
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

A Discrete Scenario Based time series for a particular data field in a Component.

# Arguments

  * `name::String`: user-defined name
  * `resolution::Dates.Period`: forecast resolution
  * `scenario_count::Int64`: Number of scenarios
  * `data::SortedDict`: timestamp - scalingfactor
  * `scaling_factor_multiplier::Union{Nothing, Function}`: Applicable when the time series data are scaling factors. Called on the associated component to convert the values.
  * `internal::InfrastructureSystemsInternal`
