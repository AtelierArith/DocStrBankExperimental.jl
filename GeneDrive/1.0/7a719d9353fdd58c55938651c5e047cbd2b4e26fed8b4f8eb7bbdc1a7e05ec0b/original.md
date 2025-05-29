```
mutable struct TemperatureSeriesData <: ExogenousChange
    node::Symbol
    times::Vector{Float64}
    values::Vector{Float64}
    set::diffeq.CallbackSet
end
```

Data for time series of temperature.

# Arguments

  * `node::Symbol`: `Node` where temperature is realized.
  * `times::Vector{Float64}`: Time step (day) of realized temperature value.
  * `values::Vector{Float64}`: Temperature in °C.
  * `set::diffeq.CallbackSet`
