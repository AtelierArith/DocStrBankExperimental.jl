```
mutable struct ReactiveRenewableControllerAB <: ReactivePowerControl
    bus_control::Int
    from_branch_control::Int
    to_branch_control::Int
    branch_id_control::String
    VC_Flag::Int
    Ref_Flag::Int
    PF_Flag::Int
    V_Flag::Int
    T_fltr::Float64
    K_p::Float64
    K_i::Float64
    T_ft::Float64
    T_fv::Float64
    V_frz::Float64
    R_c::Float64
    X_c::Float64
    K_c::Float64
    e_lim::MinMax
    dbd_pnts::Tuple{Float64, Float64}
    Q_lim::MinMax
    T_p::Float64
    Q_lim_inner::MinMax
    V_lim::MinMax
    K_qp::Float64
    K_qi::Float64
    Q_ref::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of Reactive Power Controller including REPCA1 and REECB1

# Arguments

  * `bus_control::Int`: ACBus identification [`number`](@ref ACBus) for voltage control. `0` identifies the local bus connected to this component, validation range: `(0, nothing)`
  * `from_branch_control::Int`: Monitored branch FROM bus identification number for line drop compensation (if 0 generator power will be used), validation range: `(0, nothing)`
  * `to_branch_control::Int`: Monitored branch TO bus identification number for line drop compensation (if 0 generator power will be used), validation range: `(0, nothing)`
  * `branch_id_control::String`: Branch circuit id for line drop compensation (as a string). If 0 generator power will be used
  * `VC_Flag::Int`: Voltage Compensator Flag for REPCA1, validation range: `(0, 1)`
  * `Ref_Flag::Int`: Flag for Reactive Power Control for REPCA1. 0: Q-control, 1: V-control, validation range: `(0, 1)`
  * `PF_Flag::Int`: Flag for Power Factor Control for Outer Control of REECB1. 0: Q-control, 1: Power Factor Control, validation range: `(0, 1)`
  * `V_Flag::Int`: Flag for Voltage Control for Outer Control of REECB1. 0: Voltage Control, 1: Q-Control, validation range: `(0, 1)`
  * `T_fltr::Float64`: Voltage or Q-power of REPCA Filter Time Constant, validation range: `(0, nothing)`
  * `K_p::Float64`: Reactive power PI control proportional gain, validation range: `(0, nothing)`
  * `K_i::Float64`: Reactive power PI control integral gain, validation range: `(0, nothing)`
  * `T_ft::Float64`: Reactive power lead time constant (s), validation range: `(0, nothing)`
  * `T_fv::Float64`: Reactive power lag time constant (s), validation range: `(0, nothing)`
  * `V_frz::Float64`: Voltage below which state ξq_oc (integrator state) is freeze, validation range: `(0, nothing)`
  * `R_c::Float64`: Line drop compensation resistance (used when VC_Flag = 1), validation range: `(0, nothing)`
  * `X_c::Float64`: Line drop compensation reactance (used when VC_Flag = 1), validation range: `(0, nothing)`
  * `K_c::Float64`: Reactive current compensation gain (pu) (used when VC_Flag = 0), validation range: `(0, nothing)`
  * `e_lim::MinMax`: Upper/Lower limit on Voltage or Q-power deadband output `(e_min, e_max)`
  * `dbd_pnts::Tuple{Float64, Float64}`: Voltage or Q-power error dead band thresholds `(dbd1, dbd2)`
  * `Q_lim::MinMax`: Upper/Lower limit on reactive power V/Q control in REPCA `(Q_min, Q_max)`
  * `T_p::Float64`: Active power lag time constant in REECB (s). Used only when PF_Flag = 1, validation range: `(0, nothing)`
  * `Q_lim_inner::MinMax`: Upper/Lower limit on reactive power input in REECB `(Q_min_inner, Q_max_inner)`. Only used when V_Flag = 1
  * `V_lim::MinMax`: Upper/Lower limit on reactive power PI controller in REECB `(V_min, V_max)`. Only used when V_Flag = 1
  * `K_qp::Float64`: Reactive power regulator proportional gain (used when V_Flag = 1), validation range: `(0, nothing)`
  * `K_qi::Float64`: Reactive power regulator integral gain (used when V_Flag = 1), validation range: `(0, nothing)`
  * `Q_ref::Float64`: (default: `1.0`) Reference Reactive Power Set-point (pu), validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ReactiveRenewableControllerAB model depends on the Flag
  * `n_states::Int`: (**Do not modify.**) The states of the ReactiveRenewableControllerAB model depends on the Flag
