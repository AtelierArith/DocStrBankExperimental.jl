```
mutable struct RenewableDispatch <: RenewableGen
    name::String
    available::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    reactive_power_limits::Union{Nothing, MinMax}
    power_factor::Float64
    operation_cost::Union{RenewableGenerationCost, MarketBidCost}
    base_power::Float64
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A renewable (e.g., wind or solar) generator whose output can be curtailed to satisfy power system constraints.

These generators can also participate in reserves markets, including upwards reserves by proactively curtailing some available power (based on its [`max_active_power` time series](@ref ts_data)). Example uses include: a utility-scale wind or solar generator whose PPA allows curtailment. For non-curtailable or must-take renewables, see [`RenewableNonDispatch`](@ref).

Renewable generators do not have a `max_active_power` parameter, which is instead calculated when calling [`get_max_active_power()`](@ref get_max_active_power(d::T) where {T <: RenewableGen})

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR), used in some production cost modeling simulations. To set the reactive power in a load flow, use `power_factor`
  * `rating::Float64`: Maximum output power rating of the unit (MVA), validation range: `(0, nothing)`
  * `prime_mover_type::PrimeMovers`: Prime mover technology according to EIA 923. Options are listed [here](@ref pm_list)
  * `reactive_power_limits::Union{Nothing, MinMax}`: Minimum and maximum reactive power limits, used in some production cost model simulations and in power flow if the unit is connected to a [`PV`](@ref acbustypes_list) bus. Set to `nothing` if not applicable
  * `power_factor::Float64`: Power factor [0, 1] set-point, used in some production cost modeling and in load flow if the unit is connected to a [`PQ`](@ref acbustypes_list) bus, validation range: `(0, 1)`
  * `operation_cost::Union{RenewableGenerationCost, MarketBidCost}`: [`OperationalCost`](@ref) of generation
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
