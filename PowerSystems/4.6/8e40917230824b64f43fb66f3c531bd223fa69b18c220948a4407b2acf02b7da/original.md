```
mutable struct AVRFixed <: AVR
    Vf::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters of a AVR that returns a fixed voltage to the rotor winding

# Arguments

  * `Vf::Float64`: Fixed voltage field applied to the rotor winding in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) Fixed AVR has no [states](@ref S)
  * `n_states::Int`: (**Do not modify.**) Fixed AVR has no [states](@ref S)
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) Fixed AVR has no [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
