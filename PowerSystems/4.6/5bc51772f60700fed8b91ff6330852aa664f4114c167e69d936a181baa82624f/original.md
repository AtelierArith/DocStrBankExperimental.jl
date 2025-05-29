```
mutable struct CurrentModeControl <: InnerControl
    kpc::Float64
    kic::Float64
    kffv::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of an inner loop proportional integral (PI) current control based on ["Reduced-order Structure-preserving Model for Parallel-connected Three-phase Grid-tied Inverters."](https://doi.org/10.1109/COMPEL.2017.8013389)

# Arguments

  * `kpc::Float64`: Current controller proportional gain, validation range: `(0, nothing)`
  * `kic::Float64`: Current controller integral gain, validation range: `(0, nothing)`
  * `kffv::Float64`: Gain to enable feed-forward gain of voltage, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the CurrentModeControl model are:

```
γd_ic: d-axis integrator state of the PI current controller,
γq_ic: q-axis integrator state of the PI current controller
```

  * `n_states::Int`: (**Do not modify.**) CurrentControl has 2 states
