```
mutable struct TemperatureShockData <: ExogenousChange
    node::Symbol
    times::Vector{Tuple{Float64, Float64}}
    values::Union{Float64, Vector{Float64}}
    set::diffeq.CallbackSet
end
```

Data for temperature shocks.

# Arguments

  * `node::Symbol`: `Node` where temperature shock occurs.
  * `times::Vector{Tuple{Float64,Float64}}`: Vector of tuples defining shock start/stop time points. Multiple discrete shock periods may be included.
  * `values::Union{Float64, Vector{Float64}}`: Single fixed temperature value in °C or vector of variable temperature values in °C added to the baseline temperature during the specified time period. Multiple discrete temperature changes may be included; values may be positive or negative.
  * `set::diffeq.CallbackSet`
