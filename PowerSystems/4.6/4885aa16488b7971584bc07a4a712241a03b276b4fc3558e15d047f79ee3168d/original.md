```
mutable struct DynamicExponentialLoad <: DynamicInjection
    name::String
    a::Float64
    b::Float64
    α::Float64
    β::Float64
    T_p::Float64
    T_q::Float64
    ext::Dict{String, Any}
    base_power::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 2-states of a generic dynamic load model based on ["Voltage stability analysis using generic dynamic load models."](https://doi.org/10.1109/59.317575)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `a::Float64`: Active power static exponential coefficient, validation range: `(0, nothing)`
  * `b::Float64`: Reactive power static exponential coefficient, validation range: `(0, nothing)`
  * `α::Float64`: Active power transient exponential coefficient, validation range: `(0, nothing)`
  * `β::Float64`: Reactive power transient exponential coefficient, validation range: `(0, nothing)`
  * `T_p::Float64`: Active Power Time Constant, validation range: `(0, nothing)`
  * `T_q::Float64`: Reactive Power Time Constant, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `base_power::Float64`: Base power of the load (MVA) for [per unitization](@ref per_unit)
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
x_p: Integrator state of the active power,
x_q: Integrator state of the reactive power,
```

  * `n_states::Int`: (**Do not modify.**) DynamicExponentialLoad has 2 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
