```
mutable struct Probabilistic <: Forecast
    name::String
    resolution::Dates.Period
    percentiles::Vector{Float64}
    data::SortedDict
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

A Probabilistic forecast for a particular data field in a Component.

# Arguments

  * `name::String`: user-defined name
  * `resolution::Dates.Period`: forecast resolution
  * `percentiles::Vector{Float64}`: Percentiles for the probabilistic forecast
  * `data::SortedDict`: timestamp - scalingfactor
  * `scaling_factor_multiplier::Union{Nothing, Function}`: Applicable when the time series data are scaling factors. Called on the associated component to convert the values.
  * `internal::InfrastructureSystemsInternal`
