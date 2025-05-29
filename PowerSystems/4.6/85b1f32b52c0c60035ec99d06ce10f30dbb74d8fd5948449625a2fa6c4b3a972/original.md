```
mutable struct ActiveVirtualOscillator <: ActivePowerControl
    k1::Float64
    ψ::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of an Active Virtual Oscillator controller. Model is based on ["Model Reduction for Inverters with Current Limiting and Dispatchable Virtual Oscillator Control."](https://doi.org/10.1109/TEC.2021.3083488)

# Arguments

  * `k1::Float64`: VOC Synchronization Gain, validation range: `(0, nothing)`
  * `ψ::Float64`: Rotation angle of the controller, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ActiveVirtualOscillator model are:

```
θ_oc: Phase angle displacement of the inverter model
```

  * `n_states::Int`: (**Do not modify.**) ActiveVirtualOscillator has one state
