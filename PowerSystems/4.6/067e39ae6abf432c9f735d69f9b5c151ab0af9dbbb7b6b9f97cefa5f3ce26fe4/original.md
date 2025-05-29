```
mutable struct VariableReserveNonSpinning <: ReserveNonSpinning
    name::String
    available::Bool
    time_frame::Float64
    requirement::Float64
    sustained_time::Float64
    max_output_fraction::Float64
    max_participation_factor::Float64
    deployed_fraction::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A non-spinning reserve product with a time-varying procurement requirement, such as a higher requirement during hours with an expected high load or high ramp.

This reserve product includes back-up generators that might not be currently synchronized with the power system, but can come online quickly after an unexpected contingency, such as a transmission line or generator outage. To model the time varying requirement, a ["`requirement`" time series should be added](@ref ts_data) to this reserve.

This is only an upwards reserve. For faster-responding upwards or downwards reserves from components already synchronized with the system, see [`VariableReserve`](@ref)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `time_frame::Float64`: the saturation time_frame in minutes to provide reserve contribution, validation range: `(0, nothing)`
  * `requirement::Float64`: the required quantity of the product should be scaled by a TimeSeriesData
  * `sustained_time::Float64`: (default: `14400.0`) the time in seconds reserve contribution must sustained at a specified level, validation range: `(0, nothing)`
  * `max_output_fraction::Float64`: (default: `1.0`) the maximum fraction of each device's output that can be assigned to the service, validation range: `(0, 1)`
  * `max_participation_factor::Float64`: (default: `1.0`) the maximum portion [0, 1.0] of the reserve that can be contributed per device, validation range: `(0, 1)`
  * `deployed_fraction::Float64`: (default: `0.0`) Fraction of service procurement that is assumed to be actually deployed. Most commonly, this is assumed to be either 0.0 or 1.0, validation range: `(0, 1)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
