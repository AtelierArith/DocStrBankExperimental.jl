```
mutable struct InstantaneousOutputCurrentLimiter <: OutputCurrentLimiter
    Id_max::Float64
    Iq_max::Float64
    ext::Dict{String, Any}
end
```

Parameters of Instantaneous (Square) Current Controller Limiter. Regulates inverter output current on the d and q axis separately

# Arguments

  * `Id_max::Float64`: Maximum limit on d-axis current controller input current in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `Iq_max::Float64`: Maximum limit on d-axis current controller input current in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
