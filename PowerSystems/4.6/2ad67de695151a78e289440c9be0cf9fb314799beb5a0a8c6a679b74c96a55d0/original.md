```
mutable struct TwoTerminalHVDCLine <: ACBranch
    name::String
    available::Bool
    active_power_flow::Float64
    arc::Arc
    active_power_limits_from::MinMax
    active_power_limits_to::MinMax
    reactive_power_limits_from::MinMax
    reactive_power_limits_to::MinMax
    loss::Union{LinearCurve, PiecewiseIncrementalCurve}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A High Voltage DC line, which must be connected to an [`ACBus`](@ref) on each end.

This model is appropriate for operational simulations with a linearized DC power flow approximation with losses proportional to the power flow. For modeling a DC network, see [`TModelHVDCLine`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow::Float64`: Initial condition of active power flow on the line (MW)
  * `arc::Arc`: An [`Arc`](@ref) defining this line `from` a bus `to` another bus
  * `active_power_limits_from::MinMax`: Minimum and maximum active power flows to the FROM node (MW)
  * `active_power_limits_to::MinMax`: Minimum and maximum active power flows to the TO node (MW)
  * `reactive_power_limits_from::MinMax`: Minimum and maximum reactive power limits to the FROM node (MVAR)
  * `reactive_power_limits_to::MinMax`: Minimum and maximum reactive power limits to the TO node (MVAR)
  * `loss::Union{LinearCurve, PiecewiseIncrementalCurve}`: (default: `LinearCurve(0.0)`) Loss model coefficients. It accepts a linear model with a constant loss (MW) and a proportional loss rate (MW of loss per MW of flow). It also accepts a Piecewise loss, with N segments to specify different proportional losses for different segments.
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
