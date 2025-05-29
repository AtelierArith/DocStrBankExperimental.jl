```
mutable struct ReactiveVirtualOscillator <: ReactivePowerControl
    k2::Float64
    V_ref::Float64
    Q_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Reactive Virtual Oscillator controller. Model is based on ["Model Reduction for Inverters with Current Limiting and Dispatchable Virtual Oscillator Control."](https://doi.org/10.1109/TEC.2021.3083488)

# Arguments

  * `k2::Float64`: VOC voltage-amplitude control gain, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `Q_ref::Float64`: (default: `1.0`) Reference Reactive Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ReactiveVirtualOscilator model are:

```
E_oc: voltage reference state for inner control in the d-axis
```

  * `n_states::Int`: (**Do not modify.**) ReactiveVirtualOscillator has 1 state
