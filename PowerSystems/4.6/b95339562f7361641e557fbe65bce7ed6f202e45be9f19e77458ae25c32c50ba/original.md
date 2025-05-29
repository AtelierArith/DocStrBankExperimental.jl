```
mutable struct AVRSimple <: AVR
    Kv::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters of a simple proportional AVR in the derivative of EMF i.e. an integrator controller on EMF

# Arguments

  * `Kv::Float64`: Proportional Gain, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vf: field voltage
```

  * `n_states::Int`: (**Do not modify.**) Fixed AVR has 1 [state](@ref S)
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) Simple AVR has 1 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
