```
mutable struct OuterControl{
    A <: ActivePowerControl,
    R <: ReactivePowerControl
} <: DynamicInverterComponent
    active_power_control::A
    reactive_power_control::R
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a Outer-Loop controller using a active power controller and a reactive power droop controller.

# Arguments

  * `A <: ActivePowerControl`: Active power controller (typically droop or virtual inertia).
  * `R <: ReactivePowerControl`: Reactive power controller (typically droop).
  * `ext::Dict{String, Any}`
  * `states::Vector{Symbol}`: Vector of states (will depend on the components).
  * `n_states::Int`: Number of states (will depend on the components).
