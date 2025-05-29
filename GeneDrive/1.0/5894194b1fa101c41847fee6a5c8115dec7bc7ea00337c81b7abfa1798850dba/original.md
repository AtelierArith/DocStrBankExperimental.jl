```
mutable struct ScenarioTemperature <: Temperature end
```

Data for simulation that uses ensembles of temperature time series in °C.

# Arguments

  * `data::Matrix{Float64}`: Array of ensemble members, each column of which is a time series of temperature values in °C.
  * `probability::Vector{Float64}`: Vector of probabilities with which given scenarios are expected to occur (one probability applicable per ensemble member).
  * `selected_scenario::Int`: Index to run dynamic model over selected scenarios; `Int` argument required. For decision model, use `nothing`.
