```
mutable struct GenericDER <: DynamicInjection
    name::String
    Qref_Flag::Int
    PQ_Flag::Int
    Gen_Flag::Int
    PerOp_Flag::Int
    Recon_Flag::Int
    Trv::Float64
    VV_pnts::NamedTuple{(:V1, :V2, :V3, :V4), Tuple{Float64, Float64, Float64, Float64}}
    Q_lim::MinMax
    Tp::Float64
    e_lim::MinMax
    Kpq::Float64
    Kiq::Float64
    Iqr_lim::MinMax
    I_max::Float64
    Tg::Float64
    kWh_Cap::Float64
    SOC_ini::Float64
    SOC_lim::MinMax
    Trf::Float64
    fdbd_pnts::NamedTuple{(:fdbd1, :fdbd2), Tuple{Float64, Float64}}
    D_dn::Float64
    D_up::Float64
    fe_lim::MinMax
    Kpp::Float64
    Kip::Float64
    P_lim::MinMax
    dP_lim::MinMax
    T_pord::Float64
    rrpwr::Float64
    VRT_pnts::NamedTuple{(:vrt1, :vrt2, :vrt3, :vrt4, :vrt5), Tuple{Float64, Float64, Float64, Float64, Float64}}
    TVRT_pnts::NamedTuple{(:tvrt1, :tvrt2, :tvrt3), Tuple{Float64, Float64, Float64}}
    tV_delay::Float64
    VES_lim::MinMax
    FRT_pnts::NamedTuple{(:frt1, :frt2, :frt3, :frt4), Tuple{Float64, Float64, Float64, Float64}}
    TFRT_pnts::NamedTuple{(:tfrt1, :tfrt2), Tuple{Float64, Float64}}
    tF_delay::Float64
    FES_lim::MinMax
    Pfa_ref::Float64
    Q_ref::Float64
    P_ref::Float64
    base_power::Float64
    states::Vector{Symbol}
    n_states::Int
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

Parameters of a Generic Distributed Energy Resource Model. Based on ["Modeling Framework and Coordination of DER and Flexible Loads for Ancillary Service Provision."](http://hdl.handle.net/10125/70994)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `Qref_Flag::Int`: Reactive Power Control Mode. 1 VoltVar Control, 2 Constant Q Control, 3 Constant PF Control, validation range: `(1, 3)`
  * `PQ_Flag::Int`: Active and reactive power priority mode. 0 for Q priority, 1 for P priority, validation range: `(0, 1)`
  * `Gen_Flag::Int`: Define generator or storage system. 0 unit is a storage device, 1 unit is a generator, validation range: `(0, 1)`
  * `PerOp_Flag::Int`: Defines operation of permisible region in VRT characteristic. 0 for cease, 1 for continuous operation, validation range: `(0, 1)`
  * `Recon_Flag::Int`: Defines if DER can reconnect after voltage ride-through disconnection, validation range: `(0, 1)`
  * `Trv::Float64`: Voltage measurement transducer's time constant, in s, validation range: `(0, nothing)`
  * `VV_pnts::NamedTuple{(:V1, :V2, :V3, :V4), Tuple{Float64, Float64, Float64, Float64}}`: Y-axis Volt-var curve points (V1,V2,V3,V4)
  * `Q_lim::MinMax`: Reactive power limits in pu (Q*min, Q*max)
  * `Tp::Float64`: Power measurement transducer's time constant, in s, validation range: `(0, nothing)`
  * `e_lim::MinMax`: Error limit in PI controller for q control (e*min, e*max)
  * `Kpq::Float64`: PI controller proportional gain for q control, validation range: `(0, nothing)`
  * `Kiq::Float64`: PI controller integral gain for q control, validation range: `(0, nothing)`
  * `Iqr_lim::MinMax`: Limit on rate of change for reactive current (pu/s) (Iqr*min, Iqr*max)
  * `I_max::Float64`: Max. inverter's current, validation range: `(0, nothing)`
  * `Tg::Float64`: Current control's time constant, in s, validation range: `(0, nothing)`
  * `kWh_Cap::Float64`: BESS capacity in kWh, validation range: `(0, nothing)`
  * `SOC_ini::Float64`: Initial state of charge (SOC) in pu, validation range: `(0, 1)`
  * `SOC_lim::MinMax`: Battery's SOC limits (SOC*min, SOC*max)
  * `Trf::Float64`: Time constant to estimate system frequency, in s, validation range: `(0, nothing)`
  * `fdbd_pnts::NamedTuple{(:fdbd1, :fdbd2), Tuple{Float64, Float64}}`: Frequency error dead band thresholds `(fdbd1, fdbd2)`
  * `D_dn::Float64`: reciprocal of droop for over-frequency conditions, in pu, validation range: `(0, nothing)`
  * `D_up::Float64`: reciprocal of droop for under-frequency conditions, in pu, validation range: `(0, nothing)`
  * `fe_lim::MinMax`: Frequency error limits in pu (fe*min, fe*max)
  * `Kpp::Float64`: PI controller proportional gain for p control, validation range: `(0, nothing)`
  * `Kip::Float64`: PI controller integral gain for p control, validation range: `(0, nothing)`
  * `P_lim::MinMax`: Active power limits in pu (P*min, P*max)
  * `dP_lim::MinMax`: Ramp rate limits for active power in pu/s (dP*min, dP*max)
  * `T_pord::Float64`: Power filter time constant in s, validation range: `(0, nothing)`
  * `rrpwr::Float64`: Ramp rate for real power increase following a fault, in pu/s, validation range: `(0, nothing)`
  * `VRT_pnts::NamedTuple{(:vrt1, :vrt2, :vrt3, :vrt4, :vrt5), Tuple{Float64, Float64, Float64, Float64, Float64}}`: Voltage ride through v points (vrt1,vrt2,vrt3,vrt4,vrt5)
  * `TVRT_pnts::NamedTuple{(:tvrt1, :tvrt2, :tvrt3), Tuple{Float64, Float64, Float64}}`: Voltage ride through time points (tvrt1,tvrt2,tvrt3)
  * `tV_delay::Float64`: Time delay for reconnection after voltage ride-through disconnection, validation range: `(0, nothing)`
  * `VES_lim::MinMax`: Min and max voltage for entering service (VES*min,VES*max)
  * `FRT_pnts::NamedTuple{(:frt1, :frt2, :frt3, :frt4), Tuple{Float64, Float64, Float64, Float64}}`: Frequency ride through v points (frt1,frt2,frt3,frt4)
  * `TFRT_pnts::NamedTuple{(:tfrt1, :tfrt2), Tuple{Float64, Float64}}`: Frequency ride through time points (tfrt1,tfrt2)
  * `tF_delay::Float64`: Time delay for reconnection after frequency ride-through disconnection, validation range: `(0, nothing)`
  * `FES_lim::MinMax`: Min and max frequency for entering service (FES*min,FES*max)
  * `Pfa_ref::Float64`: (default: `0.0`) Reference power factor, validation range: `(0, nothing)`
  * `Q_ref::Float64`: (default: `0.0`) Reference reactive power, in pu, validation range: `(0, nothing)`
  * `P_ref::Float64`: (default: `1.0`) Reference active power, in pu, validation range: `(0, nothing)`
  * `base_power::Float64`: (default: `100.0`) Base power of the unit (MVA) for [per unitization](@ref per_unit)
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of GenericDER depend on the Flags
  * `n_states::Int`: (**Do not modify.**) The [states](@ref S) of GenericDER depend on the Flags
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
