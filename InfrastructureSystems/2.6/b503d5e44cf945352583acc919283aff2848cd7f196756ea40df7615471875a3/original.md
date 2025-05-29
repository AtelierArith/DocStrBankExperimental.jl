```
mutable struct DeterministicSingleTimeSeries <: AbstractDeterministic
    single_time_series::SingleTimeSeries
    initial_timestamp::Dates.DateTime
    interval::Dates.Period
    count::Int
    horizon::Int
end
```

A deterministic forecast that wraps a [`SingleTimeSeries`](@ref)

`DeterministicSingleTimeSeries` behaves exactly like a [`Deterministic`](@ref), but instead of storing windows at each initial time it provides a view into the existing `SingleTimeSeries` at incrementing offsets. This avoids large data duplications when  there are the overlapping windows between forecasts. 

Can be used as a perfect forecast based on historical data when real forecast data is unavailable. 

# Arguments

  * `single_time_series::SingleTimeSeries`: wrapped `SingleTimeSeries` object
  * `initial_timestamp::Dates.DateTime`: time series availability time
  * `interval::Dates.Period`: time step between forecast windows
  * `count::Int`: number of forecast windows
  * `horizon::Int`: length of this time series
