```
mutable struct RECurrentControlB <: InnerControl
    Q_Flag::Int
    PQ_Flag::Int
    Vdip_lim::MinMax
    T_rv::Float64
    dbd_pnts::Tuple{Float64, Float64}
    K_qv::Float64
    Iqinj_lim::MinMax
    V_ref0::Float64
    K_vp::Float64
    K_vi::Float64
    T_iq::Float64
    I_max::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of the Inner Control part of the REECB model in PSS/E

# Arguments

  * `Q_Flag::Int`: Q Flag used for I_qinj, validation range: `(0, 1)`
  * `PQ_Flag::Int`: PQ Flag used for the Current Limit Logic, validation range: `(0, 1)`
  * `Vdip_lim::MinMax`: Limits for Voltage Dip Logic `(Vdip, Vup)`
  * `T_rv::Float64`: Voltage Filter Time Constant, validation range: `(0, nothing)`
  * `dbd_pnts::Tuple{Float64, Float64}`: Voltage error deadband thresholds `(dbd1, dbd2)`
  * `K_qv::Float64`: Reactive current injection gain during over and undervoltage conditions, validation range: `(0, nothing)`
  * `Iqinj_lim::MinMax`: Limits for Iqinj `(I_qh1, I_ql1)`
  * `V_ref0::Float64`: User defined reference. If 0, [`PowerSimulationsDynamics.jl`](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/) initializes to initial terminal voltage, validation range: `(0, nothing)`
  * `K_vp::Float64`: Voltage regulator proportional gain (used when QFlag = 1), validation range: `(0, nothing)`
  * `K_vi::Float64`: Voltage regulator integral gain (used when QFlag = 1), validation range: `(0, nothing)`
  * `T_iq::Float64`: Time constant for low-pass filter for state q_V when QFlag = 0, validation range: `(0, nothing)`
  * `I_max::Float64`: Maximum limit on total converter current, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the RECurrentControlB depends on the Flags
  * `n_states::Int`: (**Do not modify.**) The states of the RECurrentControlB depends on the Flags
