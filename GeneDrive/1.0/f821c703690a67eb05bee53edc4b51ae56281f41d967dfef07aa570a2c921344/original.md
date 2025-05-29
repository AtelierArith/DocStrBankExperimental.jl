```
mutable struct TimeSeriesTemperature <: Temperature end
```

Data for simulation that uses temperature time series in °C.

# Arguments

  * `value::Float64`: Time series of temperature values in °C.
  * `probability::Float64`: Probability with which timeseries expected to be observed.
  * `selected_scenario::Int`
