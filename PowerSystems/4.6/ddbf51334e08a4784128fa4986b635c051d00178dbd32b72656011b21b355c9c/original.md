```
mutable struct PIDGOV <: TurbineGov
    feedback_flag::Int
    Rperm::Float64
    T_reg::Float64
    Kp::Float64
    Ki::Float64
    Kd::Float64
    Ta::Float64
    Tb::Float64
    D_turb::Float64
    gate_openings::Tuple{Float64, Float64, Float64}
    power_gate_openings::Tuple{Float64, Float64, Float64}
    G_lim::MinMax
    A_tw::Float64
    Tw::Float64
    V_lim::MinMax
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Hydro Turbine-Governor with PID controller.

# Arguments

  * `feedback_flag::Int`: Feedback signal for governor droop: 0 for electrical power, and 1 for gate position., validation range: `(0, 1)`
  * `Rperm::Float64`: Speed permanent droop parameter, validation range: `(0, nothing)`
  * `T_reg::Float64`: Speed detector time constant, validation range: `(0, nothing)`
  * `Kp::Float64`: Governor proportional gain, validation range: `(0, nothing)`
  * `Ki::Float64`: Governor integral gain, validation range: `(0, nothing)`
  * `Kd::Float64`: Governor derivative gain, validation range: `(0, nothing)`
  * `Ta::Float64`: Governor derivative time constant, validation range: `(0, nothing)`
  * `Tb::Float64`: Gate-servo time constant, validation range: `(0, nothing)`
  * `D_turb::Float64`: Turbine damping factor, validation range: `(0, nothing)`
  * `gate_openings::Tuple{Float64, Float64, Float64}`: Gate-opening speed at different loads
  * `power_gate_openings::Tuple{Float64, Float64, Float64}`: Power at gate_openings
  * `G_lim::MinMax`: Minimum/Maximum Gate openings `(G_min, G_max)`.
  * `A_tw::Float64`: Factor multiplying Tw, validation range: `(eps(), nothing)`
  * `Tw::Float64`: Water inertia time constant, sec, validation range: `(eps(), nothing)`
  * `V_lim::MinMax`: Gate opening velocity limits `(G_min, G_max)`.
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the PIDGOV model are:

```
x_g1: Filtered input measurement,
x_g2: PI block internal state,
x_g3: First regulator state, 
x_g4: Derivative block internal state, 
x_g5: Second regulator state, 
x_g6: Gate position state, 
x_g7: Water inertia state
```

  * `n_states::Int`: (**Do not modify.**) PIDGOV has 7 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) PIDGOV has 7 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
