```
mutable struct ReserveDemandCurve{T <: ReserveDirection} <: Reserve{T}
    variable::Union{Nothing, TimeSeriesKey, CostCurve{PiecewiseIncrementalCurve}}
    name::String
    available::Bool
    time_frame::Float64
    sustained_time::Float64
    max_participation_factor::Float64
    deployed_fraction::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A reserve product with an [Operating Reserve Demand Curve (ORDC)](https://hepg.hks.harvard.edu/files/hepg/files/ordcupdate-final.pdf) for operational simulations.

The ORDC is modeled as a discretized set of `(Reserve capacity (MW), Price ($/MWh))` steps, which can vary with time. Use [`set_variable_cost!`](@ref) to define the ORDCs.

When defining the reserve, the `ReserveDirection` must be specified to define this as a [`ReserveUp`](@ref), [`ReserveDown`](@ref), or [`ReserveSymmetric`](@ref)

# Arguments

  * `variable::Union{Nothing, TimeSeriesKey, CostCurve{PiecewiseIncrementalCurve}}`: Create this object with `variable` = `nothing`, then add assign a cost curve or time-series of `variable_cost` using the [`set_variable_cost!`](@ref) function, which will automatically update this parameter
  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `time_frame::Float64`: the saturation time_frame in minutes to provide reserve contribution, validation range: `(0, nothing)`
  * `sustained_time::Float64`: (default: `3600.0`) the time in seconds that the reserve contribution must sustained at a specified level, validation range: `(0, nothing)`
  * `max_participation_factor::Float64`: (default: `1.0`) the maximum portion [0, 1.0] of the reserve that can be contributed per device, validation range: `(0, 1)`
  * `deployed_fraction::Float64`: (default: `0.0`) Fraction of service procurement that is assumed to be actually deployed. Most commonly, this is assumed to be either 0.0 or 1.0, validation range: `(0, 1)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
