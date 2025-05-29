```
mutable struct HybridSystem <: StaticInjectionSubsystem
    name::String
    available::Bool
    status::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    base_power::Float64
    operation_cost::MarketBidCost
    thermal_unit::Union{Nothing, ThermalGen}
    electric_load::Union{Nothing, ElectricLoad}
    storage::Union{Nothing, Storage}
    renewable_unit::Union{Nothing, RenewableGen}
    interconnection_impedance::ComplexF64
    interconnection_rating::Union{Nothing, Float64}
    input_active_power_limits::Union{Nothing, MinMax}
    output_active_power_limits::Union{Nothing, MinMax}
    reactive_power_limits::Union{Nothing, MinMax}
    interconnection_efficiency::Union{
        Nothing,
        NamedTuple{(:in, :out), Tuple{Float64, Float64}},
    }
    services::Vector{Service}
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A Hybrid System that includes a combination of renewable generation, load, thermal generation and/or energy storage.

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `status::Bool`: Initial commitment condition at the start of a simulation (`true` = on or `false` = off)
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR)
  * `base_power::Float64`: Base power of the unit (MVA) for per unitization, which is commonly the same as `rating`
  * `operation_cost::MarketBidCost`: Market bid cost to operate, [`MarketBidCost`](@ref)
  * `thermal_unit::Union{Nothing, ThermalGen}`: A thermal generator with supertype [`ThermalGen`](@ref)
  * `electric_load::Union{Nothing, ElectricLoad}`: A load with supertype [`ElectricLoad`](@ref)
  * `storage::Union{Nothing, Storage}`: An energy storage system with supertype [`Storage`](@ref)
  * `renewable_unit::Union{Nothing, RenewableGen}`: A renewable generator with supertype [`RenewableGen`](@ref)
  * `interconnection_impedance::ComplexF64`: Impedance (typically in p.u.) between the hybrid system and the grid interconnection
  * `interconnection_rating::Union{Nothing, Float64}`: Maximum rating of the hybrid system's interconnection with the transmission network (MVA)
  * `input_active_power_limits::MinMax`: Minimum and maximum stable input active power levels (MW)
  * `output_active_power_limits::MinMax`: Minimum and maximum stable output active power levels (MW)
  * `reactive_power_limits::Union{Nothing, MinMax}`: Minimum and maximum reactive power limits (MVAR). Set to `Nothing` if not applicable.
  * `interconnection_efficiency::Union{Nothing, NamedTuple{(:in, :out), Tuple{Float64, Float64}},}`: Efficiency [0, 1.0] at the grid interconnection to model losses `in` and `out` of the common DC-side conversion
  * `services::Vector{Service}`: (optional) Services that this device contributes to
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (optional) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (optional) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference.
