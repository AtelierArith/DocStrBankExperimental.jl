```
mutable struct ActivePowerPI <: ActivePowerControl
    Kp_p::Float64
    Ki_p::Float64
    ωz::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Proportional-Integral Active Power controller for a specified power reference

# Arguments

  * `Kp_p::Float64`: Proportional Gain, validation range: `(0, nothing)`
  * `Ki_p::Float64`: Integral Gain, validation range: `(0, nothing)`
  * `ωz::Float64`: filter frequency cutoff, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ActivePowerPI model are:

```
σp_oc: Integrator state of the PI Controller,
p_oc: Measured active power of the inverter model
```

  * `n_states::Int`: (**Do not modify.**) ActivePowerPI has two states
