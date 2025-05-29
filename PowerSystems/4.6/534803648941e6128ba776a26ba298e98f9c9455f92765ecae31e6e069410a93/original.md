```
mutable struct MagnitudeOutputCurrentLimiter <: OutputCurrentLimiter
    I_max::Float64
    ext::Dict{String, Any}
end
```

Parameters of Magnitude (Circular) Current Controller Limiter. Regulates only the magnitude of the inverter output current

# Arguments

  * `I_max::Float64`: Maximum limit on current controller input current in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
