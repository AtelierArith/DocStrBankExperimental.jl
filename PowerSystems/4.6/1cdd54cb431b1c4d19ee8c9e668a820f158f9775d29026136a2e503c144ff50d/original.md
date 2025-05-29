```
mutable struct ActivePowerDroop <: ActivePowerControl
    Rp::Float64
    ωz::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of an Active Power droop controller

# Arguments

  * `Rp::Float64`: Droop Gain, validation range: `(0, nothing)`
  * `ωz::Float64`: filter frequency cutoff, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ActivePowerDroop model are:

```
θ_oc: Phase angle displacement of the inverter model,
p_oc: Measured active power of the inverter model
```

  * `n_states::Int`: (**Do not modify.**) ActivePowerDroop has two states
