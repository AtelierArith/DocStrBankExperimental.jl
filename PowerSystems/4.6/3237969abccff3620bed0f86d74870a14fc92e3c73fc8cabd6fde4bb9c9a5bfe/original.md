```
mutable struct GeneralGovModel <: TurbineGov
    Rselect::Int
    fuel_flag::Int
    R::Float64
    Tpelec::Float64
    speed_error_signal::MinMax
    Kp_gov::Float64
    Ki_gov::Float64
    Kd_gov::Float64
    Td_gov::Float64
    valve_position_limits::MinMax
    T_act::Float64
    K_turb::Float64
    Wf_nl::Float64
    Tb::Float64
    Tc::Float64
    T_eng::Float64
    Tf_load::Float64
    Kp_load::Float64
    Ki_load::Float64
    Ld_ref::Float64
    Dm::Float64
    R_open::Float64
    R_close::Float64
    Ki_mw::Float64
    A_set::Float64
    Ka::Float64
    Ta::Float64
    T_rate::Float64
    db::Float64
    Tsa::Float64
    Tsb::Float64
    R_lim::UpDown
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

GE General Governor/Turbine Model. The GeneralGovModel (GGOV1) model is a general purpose governor model used for a variety of prime movers controlled by proportional-integral-derivative (PID) governors including gas turbines

# Arguments

  * `Rselect::Int`: Feedback signal for governor droop, validation range: `(-2, 1)`
  * `fuel_flag::Int`: Flag Switch for fuel source characteristic, validation range: `(0, 1)`
  * `R::Float64`: Speed droop parameter, validation range: `(eps(), nothing)`
  * `Tpelec::Float64`: Electrical power transducer time constant, seconds, validation range: `(eps(), nothing)`
  * `speed_error_signal::MinMax`: Speed error signal limits
  * `Kp_gov::Float64`: Governor proportional gain, validation range: `(0, nothing)`
  * `Ki_gov::Float64`: Governor integral gain, validation range: `(0, nothing)`
  * `Kd_gov::Float64`: Governor derivative gain, validation range: `(0, nothing)`
  * `Td_gov::Float64`: Governor derivative time constant, validation range: `(0, nothing)`
  * `valve_position_limits::MinMax`: Valve position limits
  * `T_act::Float64`: Actuator time constant, validation range: `(0, nothing)`
  * `K_turb::Float64`: Turbine gain, validation range: `(0, nothing)`
  * `Wf_nl::Float64`: No load fuel flow, pu, validation range: `(0, nothing)`
  * `Tb::Float64`: Turbine lag time constant, sec, validation range: `(0, nothing)`
  * `Tc::Float64`: Turbine lead time constant, sec, validation range: `(0, nothing)`
  * `T_eng::Float64`: Transport lag time constant for diesel engine, sec, validation range: `(0, nothing)`
  * `Tf_load::Float64`: Load limiter time constant, validation range: `(0, nothing)`
  * `Kp_load::Float64`: Load limiter proportional gain for PI controller, validation range: `(0, nothing)`
  * `Ki_load::Float64`: Load integral gain for PI controller, validation range: `(0, nothing)`
  * `Ld_ref::Float64`: Load limiter integral gain for PI controller, validation range: `(0, nothing)`
  * `Dm::Float64`: Mechanical damping coefficient, pu, validation range: `(0, nothing)`
  * `R_open::Float64`: Maximum valve opening rate, pu/sec, validation range: `(0, nothing)`
  * `R_close::Float64`: Maximum valve closing rate, pu/sec, validation range: `(0, nothing)`
  * `Ki_mw::Float64`: Power controller (reset) gain, validation range: `(0, nothing)`
  * `A_set::Float64`: Acceleration limiter setpoint, pu/sec, validation range: `(0, nothing)`
  * `Ka::Float64`: Acceleration limiter gain, validation range: `(0, nothing)`
  * `Ta::Float64`: Acceleration limiter time constant , validation range: `(eps(), nothing)`
  * `T_rate::Float64`: Turbine rating, validation range: `(0, nothing)`
  * `db::Float64`: Speed governor deadband, validation range: `(0, nothing)`
  * `Tsa::Float64`: Temperature detection lead time constant, validation range: `(0, nothing)`
  * `Tsb::Float64`: Temperature detection lag time constant, validation range: `(0, nothing)`
  * `R_lim::UpDown`: Maximum rate of load increase
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the GGOV1 model are:

```
Pe: Machine Electrical Power Measurement,
x_g1: Governor differential control,
x_g2: Governor integral control, 
x_g3: Turbine actuator, 
x_g4: Turbine Lead-Lag, 
x_g5: Turbine load limiter measurement, 
x_g6: Turbine Load Limiter Integral Control, 
x_g7: Supervisory Load Control, 
x_g8: Acceleration Control, 
x_g9 Temperature Detection Lead - Lag:
```

  * `n_states::Int`: (**Do not modify.**) GeneralGovModel has 10 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) GGOV1 has 10 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
