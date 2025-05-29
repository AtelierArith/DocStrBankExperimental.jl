```
mutable struct VirtualInertia <: ActivePowerControl
    Ta::Float64
    kd::Float64
    kω::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Virtual Inertia with SRF using VSM for active power controller

# Arguments

  * `Ta::Float64`: VSM inertia constant, validation range: `(0, nothing)`
  * `kd::Float64`: VSM damping constant, validation range: `(0, nothing)`
  * `kω::Float64`: frequency droop gain, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the VirtualInertia model are:

```
θ_oc: Phase angle displacement of the virtual synchronous generator model
ω_oc: Speed of the rotating reference frame of the virtual synchronous generator model
```

  * `n_states::Int`: (**Do not modify.**) VirtualInertia has two states
