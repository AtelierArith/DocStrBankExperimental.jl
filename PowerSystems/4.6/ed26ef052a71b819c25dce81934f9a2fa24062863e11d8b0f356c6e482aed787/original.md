```
mutable struct AggregateDistributedGenerationA <: DynamicInjection
    name::String
    Pf_Flag::Int
    Freq_Flag::Int
    PQ_Flag::Int
    Gen_Flag::Int
    Vtrip_Flag::Int
    Ftrip_Flag::Int
    T_rv::Float64
    Trf::Float64
    dbd_pnts::Tuple{Float64, Float64}
    K_qv::Float64
    Tp::Float64
    T_iq::Float64
    D_dn::Float64
    D_up::Float64
    fdbd_pnts::Tuple{Float64, Float64}
    fe_lim::MinMax
    P_lim::MinMax
    dP_lim::MinMax
    Tpord::Float64
    Kpg::Float64
    Kig::Float64
    I_max::Float64
    vl_pnts::Vector{Tuple{Float64,Float64}}
    vh_pnts::Vector{Tuple{Float64,Float64}}
    Vrfrac::Float64
    fl::Float64
    fh::Float64
    tfl::Float64
    tfh::Float64
    Tg::Float64
    rrpwr::Float64
    Tv::Float64
    Vpr::Float64
    Iq_lim::MinMax
    V_ref::Float64
    Pfa_ref::Float64
    ω_ref::Float64
    Q_ref::Float64
    P_ref::Float64
    base_power::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of the DERA1 model in PSS/E

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `Pf_Flag::Int`: Flag for Power Factor Control, validation range: `(0, 1)`
  * `Freq_Flag::Int`: Flag to enable/disable frequency control, validation range: `(0, 1)`
  * `PQ_Flag::Int`: Flag used to enforce maximum current, validation range: `(0, 1)`
  * `Gen_Flag::Int`: Flag to specify generator or storage, validation range: `(0, 1)`
  * `Vtrip_Flag::Int`: Flag to enable/disable voltage trip logic, validation range: `(0, 1)`
  * `Ftrip_Flag::Int`: Flag to enable/disable frequency trip logic, validation range: `(0, 1)`
  * `T_rv::Float64`: Voltage measurement transducer time constant, validation range: `(0, nothing)`
  * `Trf::Float64`: Frequency measurement transducer time constant, validation range: `(0, nothing)`
  * `dbd_pnts::Tuple{Float64, Float64}`: Voltage deadband thresholds `(dbd1, dbd2)`
  * `K_qv::Float64`: Proportional voltage control gain (pu), validation range: `(0, nothing)`
  * `Tp::Float64`: Power measurement transducer time constant, validation range: `(0, nothing)`
  * `T_iq::Float64`: Time constant for low-pass filter for state q_V when QFlag = 0, validation range: `(0, nothing)`
  * `D_dn::Float64`: Reciprocal of droop for over-frequency conditions (>0) (pu), validation range: `(0, nothing)`
  * `D_up::Float64`: Reciprocal of droop for under-frequency conditions <=0) (pu), validation range: `(0, nothing)`
  * `fdbd_pnts::Tuple{Float64, Float64}`: Frequency control deadband thresholds `(fdbd1, fdbd2)`
  * `fe_lim::MinMax`: Frequency error limits (femin, femax)
  * `P_lim::MinMax`: Power limits (Pmin, Pmax)
  * `dP_lim::MinMax`: Power reference ramp rate limits (dPmin, dPmax)
  * `Tpord::Float64`: Power filter time constant, validation range: `(0, nothing)`
  * `Kpg::Float64`: PI controller proportional gain (pu), validation range: `(0, nothing)`
  * `Kig::Float64`: PI controller integral gain (pu), validation range: `(0, nothing)`
  * `I_max::Float64`: Maximum limit on total converter current (pu), validation range: `(0, nothing)`
  * `vl_pnts::Vector{Tuple{Float64,Float64}}`: Low voltage cutout points `[(tv10, vl0), (tv11, vl1)]`
  * `vh_pnts::Vector{Tuple{Float64,Float64}}`: High voltage cutout points `[(tvh0, vh0), (tvh1, vh1)]`
  * `Vrfrac::Float64`: Fraction of device that recovers after voltage comes back to within vl1 < V < vh1 (0 <= Vrfrac <= 1), validation range: `(0, 1)`
  * `fl::Float64`: Inverter frequency break-point for low frequency cut-out (Hz), validation range: `(0, nothing)`
  * `fh::Float64`: Inverter frequency break-point for high frequency cut-out (Hz), validation range: `(0, nothing)`
  * `tfl::Float64`: Low frequency cut-out timer corresponding to frequency fl (s), validation range: `(0, nothing)`
  * `tfh::Float64`: High frequency cut-out timer corresponding to frequency fh (s), validation range: `(0, nothing)`
  * `Tg::Float64`: Current control time constant (to represent behavior of inner control loops) (> 0) (s), validation range: `(0, nothing)`
  * `rrpwr::Float64`: Ramp rate for real power increase following a fault (pu/s), validation range: `(0, nothing)`
  * `Tv::Float64`: Time constant on the output of the multiplier (s), validation range: `(0, nothing)`
  * `Vpr::Float64`: Voltage below which frequency tripping is disabled (pu), validation range: `(0, nothing)`
  * `Iq_lim::MinMax`: Reactive current injection limits (Iqll, Iqhl)
  * `V_ref::Float64`: (default: `1.0`) User defined voltage reference. If 0, [`PowerSimulationsDynamics.jl`](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/) initializes to initial terminal voltage, validation range: `(0, nothing)`
  * `Pfa_ref::Float64`: (default: `0.0`) Reference power factor, validation range: `(0, nothing)`
  * `ω_ref::Float64`: (default: `1.0`) Reference Frequency (pu), validation range: `(0, nothing)`
  * `Q_ref::Float64`: (default: `0.0`) Reference reactive power, in pu, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference active power, in pu, validation range: `(0, nothing)`
  * `base_power::Float64`: (default: `100.0`) Base power (MVA) for [per unitization](@ref per_unit)
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of AggregateDistributedGenerationA depends on the Flags
  * `n_states::Int`: (**Do not modify.**) The states of AggregateDistributedGenerationA depends on the Flags
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
