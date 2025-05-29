```
mutable struct RenewableEnergyVoltageConverterTypeA <: Converter
    T_g::Float64
    Rrpwr::Float64
    Brkpt::Float64
    Zerox::Float64
    Lvpl1::Float64
    Vo_lim::Float64
    Lv_pnts::MinMax
    Io_lim::Float64
    T_fltr::Float64
    K_hv::Float64
    Iqr_lims::MinMax
    Accel::Float64
    Lvpl_sw::Int
    Q_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

Parameters of a renewable energy generator/converter model, this model corresponds to REGCA1 in PSSE, but to be interfaced using a Voltage Source instead of a Current Source

# Arguments

  * `T_g::Float64`: Converter time constant (s), validation range: `(0, nothing)`
  * `Rrpwr::Float64`: Low Voltage Power Logic (LVPL) ramp rate limit (pu/s), validation range: `(0, nothing)`
  * `Brkpt::Float64`: LVPL characteristic voltage 2 (pu), validation range: `(0, nothing)`
  * `Zerox::Float64`: LVPL characteristic voltage 1 (pu), validation range: `(0, nothing)`
  * `Lvpl1::Float64`: LVPL gain (pu), validation range: `(0, nothing)`
  * `Vo_lim::Float64`: Voltage limit for high voltage reactive current management (pu), validation range: `(0, nothing)`
  * `Lv_pnts::MinMax`: Voltage points for low voltage active current management (pu) (Lvpnt0, Lvpnt1)
  * `Io_lim::Float64`: Current limit (pu) for high voltage reactive current management (specified as a negative value), validation range: `(nothing, 0)`
  * `T_fltr::Float64`: Voltage filter time constant for low voltage active current management (s), validation range: `(0, nothing)`
  * `K_hv::Float64`: Overvoltage compensation gain used in the high voltage reactive current management, validation range: `(0, nothing)`
  * `Iqr_lims::MinMax`: Limit on rate of change for reactive current (pu/s) (Iqr*min, Iqr*max)
  * `Accel::Float64`: Acceleration factor, validation range: `(0, 1)`
  * `Lvpl_sw::Int`: Low voltage power logic (LVPL) switch. (0: LVPL not present, 1: LVPL present), validation range: `(0, 1)`
  * `Q_ref::Float64`: (default: `1.0`) Initial condition of reactive power from power flow, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:	Ip: Converter lag for Ipcmd,	Iq: Converter lag for Iqcmd,	Vmeas: Voltage filter for low voltage active current management
  * `n_states::Int`: (**Do not modify.**) RenewableEnergyVoltageConverterTypeA has 3 states
