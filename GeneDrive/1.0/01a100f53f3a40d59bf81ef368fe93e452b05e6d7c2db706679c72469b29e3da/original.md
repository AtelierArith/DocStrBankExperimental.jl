```
mutable struct NoResponse <: TemperatureResponse
    baseline_value::Float64
end
```

Data for model without temperature response.

# Arguments:

  * `baseline_value::Float64`: Literature-sourced (rather than dynamically calculated) vital rate parameter.
