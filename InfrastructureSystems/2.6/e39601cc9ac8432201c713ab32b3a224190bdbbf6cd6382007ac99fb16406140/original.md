```
mutable struct SingleTimeSeries <: StaticTimeSeries
    name::String
    data::TimeSeries.TimeArray
    scaling_factor_multiplier::Union{Nothing, Function}
    internal::InfrastructureSystemsInternal
end
```

A single column of time series data for a particular data field in a Component.

In contrast with a forecast, this can represent one continual time series, such as a series of historical measurements or realizations or a single scenario (e.g. a weather year or different input assumptions).

# Arguments

  * `name::String`: user-defined name
  * `data::TimeSeries.TimeArray`: timestamp - scalingfactor
  * `resolution::Dates.Period`: Time duration between steps in the time series. The resolution must be the same throughout the time series
  * `scaling_factor_multiplier::Union{Nothing, Function}`: Applicable when the time series data are scaling factors. Called on the associated component to convert the values.
  * `internal::InfrastructureSystemsInternal`
