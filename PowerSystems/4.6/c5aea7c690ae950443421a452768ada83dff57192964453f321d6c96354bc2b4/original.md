```
mutable struct ActiveRenewableControllerAB <: ActivePowerControl
    bus_control::Int
    from_branch_control::Int
    to_branch_control::Int
    branch_id_control::String
    Freq_Flag::Int
    K_pg::Float64
    K_ig::Float64
    T_p::Float64
    fdbd_pnts::Tuple{Float64, Float64}
    fe_lim::MinMax
    P_lim::MinMax
    T_g::Float64
    D_dn::Float64
    D_up::Float64
    dP_lim::MinMax
    P_lim_inner::MinMax
    T_pord::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of Active Power Controller including REPCA1 and REECB1

# Arguments

  * `bus_control::Int`: ACBus identification [`number`](@ref ACBus) for voltage control. `0` identifies the local bus connected to this component, validation range: `(0, nothing)`
  * `from_branch_control::Int`: Monitored branch FROM bus number for line drop compensation (if 0 generator power will be used), validation range: `(0, nothing)`
  * `to_branch_control::Int`: Monitored branch TO bus number for line drop compensation (if 0 generator power will be used), validation range: `(0, nothing)`
  * `branch_id_control::String`: Branch circuit id for line drop compensation (as a string). If 0 generator power will be used
  * `Freq_Flag::Int`: Frequency Flag for REPCA1: 0: disable, 1:enable, validation range: `(0, 1)`
  * `K_pg::Float64`: Active power PI control proportional gain, validation range: `(0, nothing)`
  * `K_ig::Float64`: Active power PI control integral gain, validation range: `(0, nothing)`
  * `T_p::Float64`: Real power measurement filter time constant (s), validation range: `(0, nothing)`
  * `fdbd_pnts::Tuple{Float64, Float64}`: Frequency error dead band thresholds `(fdbd1, fdbd2)`
  * `fe_lim::MinMax`: Upper/Lower limit on frequency error `(fe_min, fe_max)`
  * `P_lim::MinMax`: Upper/Lower limit on power reference `(P_min, P_max)`
  * `T_g::Float64`: Power Controller lag time constant, validation range: `(0, nothing)`
  * `D_dn::Float64`: Droop for over-frequency conditions, validation range: `(nothing, 0)`
  * `D_up::Float64`: Droop for under-frequency conditions, validation range: `(0, nothing)`
  * `dP_lim::MinMax`: Upper/Lower limit on power reference ramp rates`(dP_min, dP_max)`
  * `P_lim_inner::MinMax`: Upper/Lower limit on power reference for REECB`(P_min_inner, P_max_inner)`
  * `T_pord::Float64`: Power filter time constant REECB time constant, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the ActiveRenewableControllerAB model depends on the Flag
  * `n_states::Int`: (**Do not modify.**) The states of the ActiveRenewableControllerAB model depends on the Flag
