```
mutable struct ReactivePowerPI <: ReactivePowerControl
    Kp_q::Float64
    Ki_q::Float64
    ωf::Float64
    V_ref::Float64
    Q_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Proportional-Integral Reactive Power controller for a specified power reference

# Arguments

  * `Kp_q::Float64`: Proportional Gain, validation range: `(0, nothing)`
  * `Ki_q::Float64`: Integral Gain, validation range: `(0, nothing)`
  * `ωf::Float64`: filter frequency cutoff, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Voltage Set-point (pu), validation range: `(0, nothing)`
  * `Q_ref::Float64`: (default: `1.0`) Reactive Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ReactivePowerPI model are:

```
σq_oc: Integrator state of the PI Controller,
q_oc: Measured reactive power of the inverter model
```

  * `n_states::Int`: (**Do not modify.**) ReactivePowerPI has two states
