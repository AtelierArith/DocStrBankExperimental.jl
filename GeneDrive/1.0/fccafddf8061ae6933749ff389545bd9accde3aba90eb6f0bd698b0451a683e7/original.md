```
mutable struct ConstantTemperature <: Temperature end
```

Data for simulation that features a single constant temperature in °C. Generated internally.

# Arguments

  * `value::Float64`: Temperature value in °C; re-used by model at every time step.
