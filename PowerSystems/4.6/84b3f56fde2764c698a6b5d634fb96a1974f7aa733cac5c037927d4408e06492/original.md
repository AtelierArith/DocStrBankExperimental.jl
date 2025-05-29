```
mutable struct EnergyReservoirStorage <: Storage
    name::String
    available::Bool
    bus::ACBus
    prime_mover_type::PrimeMovers
    storage_technology_type::StorageTech
    storage_capacity::Float64
    storage_level_limits::MinMax
    initial_storage_capacity_level::Float64
    rating::Float64
    active_power::Float64
    input_active_power_limits::MinMax
    output_active_power_limits::MinMax
    efficiency::NamedTuple{(:in, :out), Tuple{Float64, Float64}}
    reactive_power::Float64
    reactive_power_limits::Union{Nothing, MinMax}
    base_power::Float64
    operation_cost::Union{StorageCost, MarketBidCost}
    conversion_factor::Float64
    storage_target::Float64
    cycle_limits::Int
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

An energy storage device, modeled as a generic energy reservoir.

This is suitable for modeling storage charging and discharging with average efficiency losses, ignoring the physical dynamics of the storage unit. A variety of energy storage types and chemistries can be modeled with this approach. For pumped hydro storage, alternatively see [`HydroPumpedStorage`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bus::ACBus`: Bus that this component is connected to
  * `prime_mover_type::PrimeMovers`: Prime mover technology according to EIA 923. Options are listed [here](@ref pm_list)
  * `storage_technology_type::StorageTech`: Storage Technology Complementary to EIA 923. Options are listed [here](@ref storagetech_list)
  * `storage_capacity::Float64`: Maximum storage capacity (can be in units of, e.g., MWh for batteries or liters for hydrogen), validation range: `(0, nothing)`
  * `storage_level_limits::MinMax`: Minimum and maximum allowable storage levels [0, 1], which can be used to model derates or other restrictions, such as state-of-charge restrictions on battery cycling, validation range: `(0, 1)`
  * `initial_storage_capacity_level::Float64`: Initial storage capacity level as a ratio [0, 1.0] of `storage_capacity`, validation range: `(0, 1)`
  * `rating::Float64`: Maximum output power rating of the unit (MVA)
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used
  * `input_active_power_limits::MinMax`: Minimum and maximum limits on the input active power (i.e., charging), validation range: `(0, nothing)`
  * `output_active_power_limits::MinMax`: Minimum and maximum limits on the output active power (i.e., discharging), validation range: `(0, nothing)`
  * `efficiency::NamedTuple{(:in, :out), Tuple{Float64, Float64}}`: Average efficiency [0, 1] `in` (charging/filling) and `out` (discharging/consuming) of the storage system, validation range: `(0, 1)`
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR), validation range: `reactive_power_limits`
  * `reactive_power_limits::Union{Nothing, MinMax}`: Minimum and maximum reactive power limits. Set to `Nothing` if not applicable
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `operation_cost::Union{StorageCost, MarketBidCost}`: (default: `StorageCost(nothing)`) [`OperationalCost`](@ref) of storage
  * `conversion_factor::Float64`: (default: `1.0`) Conversion factor of `storage_capacity` to MWh, if different than 1.0. For example, X MWh/liter hydrogen
  * `storage_target::Float64`: (default: `0.0`) Storage target at the end of simulation as ratio of storage capacity
  * `cycle_limits::Int`: (default: `1e4`) Storage Maximum number of cycles per year
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
