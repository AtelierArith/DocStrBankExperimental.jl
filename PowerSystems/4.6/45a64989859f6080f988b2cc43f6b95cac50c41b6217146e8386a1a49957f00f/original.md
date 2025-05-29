```
mutable struct TransmissionInterface <: Service
    name::String
    available::Bool
    active_power_flow_limits::MinMax
    violation_penalty::Float64
    direction_mapping::Dict{String, Int}
    internal::InfrastructureSystemsInternal
end
```

A collection of branches that make up an interface or corridor for the transfer of power, such as between different [`Areas`](@ref Area) or [`LoadZones`](@ref LoadZone).

The interface can be used to constrain the power flow across it

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `active_power_flow_limits::MinMax`: Minimum and maximum active power flow limits on the interface (MW)
  * `violation_penalty::Float64`: (default: `INFINITE_COST`) Penalty cost for violating the flow limits in the interface
  * `direction_mapping::Dict{String, Int}`: (default: `Dict{String, Int}()`) Dictionary of the line `name`s in the interface and their direction of flow (1 or -1) relative to the flow of the interface
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
