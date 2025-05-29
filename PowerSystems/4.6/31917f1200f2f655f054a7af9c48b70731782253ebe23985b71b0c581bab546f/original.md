```
mutable struct ActiveConstantPowerLoad <: DynamicInjection
    name::String
    r_load::Float64
    c_dc::Float64
    rf::Float64
    lf::Float64
    cf::Float64
    rg::Float64
    lg::Float64
    kp_pll::Float64
    ki_pll::Float64
    kpv::Float64
    kiv::Float64
    kpc::Float64
    kic::Float64
    base_power::Float64
    ext::Dict{String, Any}
    P_ref::Float64
    Q_ref::Float64
    V_ref::Float64
    ω_ref::Float64
    is_filter_differential::Int
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 12-[states](@ref S) active power load based on the paper, ["Dynamic Stability of a Microgrid With an Active Load."](https://doi.org/10.1109/TPEL.2013.2241455)

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `r_load::Float64`: DC-side resistor, validation range: `(0, nothing)`
  * `c_dc::Float64`: DC-side capacitor, validation range: `(0, nothing)`
  * `rf::Float64`: Converter side filter resistance, validation range: `(0, nothing)`
  * `lf::Float64`: Converter side filter inductance, validation range: `(0, nothing)`
  * `cf::Float64`: AC Converter filter capacitance, validation range: `(0, nothing)`
  * `rg::Float64`: Network side filter resistance, validation range: `(0, nothing)`
  * `lg::Float64`: Network side filter inductance, validation range: `(0, nothing)`
  * `kp_pll::Float64`: Proportional constant for PI-PLL block, validation range: `(0, nothing)`
  * `ki_pll::Float64`: Integral constant for PI-PLL block, validation range: `(0, nothing)`
  * `kpv::Float64`: Proportional constant for Voltage Control block, validation range: `(0, nothing)`
  * `kiv::Float64`: Integral constant for Voltage Control block, validation range: `(0, nothing)`
  * `kpc::Float64`: Proportional constant for Current Control block, validation range: `(0, nothing)`
  * `kic::Float64`: Integral constant for Current Control block, validation range: `(0, nothing)`
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `P_ref::Float64`: Reference active power (pu)
  * `Q_ref::Float64`: Reference reactive power (pu)
  * `V_ref::Float64`: Reference voltage (pu)
  * `ω_ref::Float64`: Reference frequency (pu)
  * `is_filter_differential::Int`: Boolean to decide if filter [states](@ref S) are differential or algebraic
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
θ_pll: PLL deviation angle, 
ϵ_pll: PLL integrator state, 
η: DC-voltage controller integrator state, 
v_dc: DC voltage at the capacitor, 
γd: d-axis Current controller integrator state, 
γq: q-axis Current controller integrator state, 
ir_cnv: Real current out of the converter,
ii_cnv: Imaginary current out of the converter,
vr_filter: Real voltage at the filter's capacitor,
vi_filter: Imaginary voltage at the filter's capacitor,
ir_filter: Real current out of the filter,
ii_filter: Imaginary current out of the filter
```

  * `n_states::Int`: (**Do not modify.**) ActiveConstantPowerLoad has 12 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
