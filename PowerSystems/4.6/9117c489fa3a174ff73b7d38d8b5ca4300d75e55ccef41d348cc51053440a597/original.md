```
mutable struct ReactivePowerDroop <: ReactivePowerControl
    kq::Float64
    ωf::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Reactive Power droop controller

# Arguments

  * `kq::Float64`: frequency droop gain, validation range: `(0, nothing)`
  * `ωf::Float64`: filter frequency cutoff, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ReactivePowerDroop model are:

```
q_oc: Filtered reactive output power
```

  * `n_states::Int`: (**Do not modify.**) ReactivePowerDroop has 1 state
