```
mutable struct AGC <: Service
    name::String
    available::Bool
    bias::Float64
    K_p::Float64
    K_i::Float64
    K_d::Float64
    delta_t::Float64
    area::Union{Nothing, Area}
    initial_ace::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

Automatic generation control (AGC) for the system or a certain `Area` within the system.

This model uses a proportional–integral–derivative (PID) control to simulate a "smooth" response of the AGC to the area control error (ACE). Refer to ["AGC Simulation Model for Large Renewable Energy Penetration Studies."](https://doi.org/10.1109/NAPS50074.2021.9449687)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `available::Bool`: Indicator of whether the component is connected and online (`true`) or disconnected, offline, or down (`false`). Unavailable components are excluded during simulations
  * `bias::Float64`: Area frequency bias in MW/Hz
  * `K_p::Float64`: PID Proportional Constant
  * `K_i::Float64`: PID Integral Constant
  * `K_d::Float64`: PID Derivative Constant
  * `delta_t::Float64`: PID Discretization period [Seconds]
  * `area::Union{Nothing, Area}`: (default: `nothing`) the area controlled by the AGC
  * `initial_ace::Float64`: (default: `0.0`) Initial condition for ACE
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
