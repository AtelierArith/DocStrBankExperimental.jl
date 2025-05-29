```
mutable struct ThermalMultiStart <: ThermalGen
    name::String
    available::Bool
    status::Bool
    bus::ACBus
    active_power::Float64
    reactive_power::Float64
    rating::Float64
    prime_mover_type::PrimeMovers
    fuel::ThermalFuels
    active_power_limits::MinMax
    reactive_power_limits::Union{Nothing, MinMax}
    ramp_limits::Union{Nothing, UpDown}
    power_trajectory::Union{Nothing, StartUpShutDown}
    time_limits::Union{Nothing, UpDown}
    start_time_limits::Union{Nothing, StartUpStages}
    start_types::Int
    operation_cost::Union{ThermalGenerationCost, MarketBidCost}
    base_power::Float64
    services::Vector{Service}
    time_at_status::Float64
    must_run::Bool
    dynamic_injector::Union{Nothing, DynamicInjection}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A thermal generator, such as a fossil fuel or nuclear generator, that can start-up again from a *hot*, *warm*, or *cold* state.

`ThermalMultiStart` has a detailed representation of the start-up process based on the time elapsed since the last shut down, as well as a detailed shut-down process. The model is based on ["Tight and Compact MILP Formulation for the Thermal Unit Commitment Problem."](https://doi.org/10.1109/TPWRS.2013.2251373). For a simplified representation of the start-up and shut-down processes, see [`ThermalStandard`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `status::Bool`: Initial commitment condition at the start of a simulation (`true` = on or `false` = off)
  * `bus::ACBus`: Bus that this component is connected to
  * `active_power::Float64`: Initial active power set point of the unit in MW. For power flow, this is the steady state operating point of the system. For production cost modeling, this may or may not be used as the initial starting point for the solver, depending on the solver used, validation range: `active_power_limits`
  * `reactive_power::Float64`: Initial reactive power set point of the unit (MVAR), validation range: `reactive_power_limits`
  * `rating::Float64`: Maximum output power rating of the unit (MVA), validation range: `(0, nothing)`
  * `prime_mover_type::PrimeMovers`: Prime mover technology according to EIA 923. Options are listed [here](@ref pm_list)
  * `fuel::ThermalFuels`: Prime mover fuel according to EIA 923. Options are listed [here](@ref tf_list)
  * `active_power_limits::MinMax`: Minimum and maximum stable active power levels (MW)
  * `reactive_power_limits::Union{Nothing, MinMax}`: Minimum and maximum reactive power limits. Set to `Nothing` if not applicable
  * `ramp_limits::Union{Nothing, UpDown}`:, validation range: `(0, nothing)`
  * `power_trajectory::Union{Nothing, StartUpShutDown}`: Power trajectory the unit will take during the start-up and shut-down ramp process, validation range: `(0, nothing)`
  * `time_limits::Union{Nothing, UpDown}`: Minimum up and Minimum down time limits in hours, validation range: `(0, nothing)`
  * `start_time_limits::Union{Nothing, StartUpStages}`: Time limits for start-up based on turbine temperature in hours
  * `start_types::Int`: Number of start-up based on turbine temperature, where `1` = *hot*, `2` = *warm*, and `3` = *cold*, validation range: `(1, 3)`
  * `operation_cost::Union{ThermalGenerationCost, MarketBidCost}`: [`OperationalCost`](@ref) of generation
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `services::Vector{Service}`: (default: `Device[]`) Services that this device contributes to
  * `time_at_status::Float64`: (default: `INFINITE_TIME`) Time (e.g., `Hours(6)`) the generator has been on or off, as indicated by `status`
  * `must_run::Bool`: (default: `false`) Set to `true` if the unit is must run
  * `dynamic_injector::Union{Nothing, DynamicInjection}`: (default: `nothing`) corresponding dynamic injection device
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
