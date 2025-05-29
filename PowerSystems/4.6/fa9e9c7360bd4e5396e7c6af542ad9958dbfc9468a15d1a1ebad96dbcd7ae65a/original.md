```
mutable struct Source <: StaticInjection
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    R_th::Float64
    X_th::Float64
    internal_voltage::Float64
    internal_angle::Float64
    base_power::Float64
    dynamic_injector::Union{Nothing, DynamicInjection}
    services::Vector{Service}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

An infinite bus with a constant voltage output.

Commonly used in dynamics simulations to represent a very large machine on a single bus

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR)
  * `R_th::Float64`: Source Thevenin resistance, validation range: `(0, nothing)`
  * `X_th::Float64`: Source Thevenin reactance, validation range: `(0, nothing)`
  * `internal_voltage::Float64`: (default: `1.0`) Internal Voltage (pu), validation range: `(0, nothing)`
  * `internal_angle::Float64`: (default: `0.0`) Internal Angle
  * `base_power::Float64`: (default: `100.0`) Base Power in MVA
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
