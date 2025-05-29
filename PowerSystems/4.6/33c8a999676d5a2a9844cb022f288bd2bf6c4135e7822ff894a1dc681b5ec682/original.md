```
mutable struct PriorityOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    ϕ_I::Float64
    ext::Dict{String, Any}
end
```

Parameters of Priority-Based Current Controller Limiter. Regulates the magnitude of the inverter output current and prioritizes a specific angle for the resultant current signal

# Arguments

  * `I_max::Float64`: Maximum limit on current controller input current in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `ϕ_I::Float64`: Pre-defined angle (measured against the d-axis) for I*ref once limit I*max is hit, validation range: `(-1.571, 1.571)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
