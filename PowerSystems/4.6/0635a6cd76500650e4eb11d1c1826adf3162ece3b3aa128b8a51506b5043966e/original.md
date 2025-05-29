```
mutable struct ESST1A <: AVR
    UEL_flags::Int
    PSS_flags::Int
    Tr::Float64
    Vi_lim::Tuple{Float64, Float64}
    Tc::Float64
    Tb::Float64
    Tc1::Float64
    Tb1::Float64
    Ka::Float64
    Ta::Float64
    Va_lim::MinMax
    Vr_lim::MinMax
    Kc::Float64
    Kf::Float64
    Tf::Float64
    K_lr::Float64
    I_lr::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

This excitation system supplies power through a transformer from the generator terminals and its regulated by a controlled rectifier (via thyristors). Parameters of IEEE Std 421.5 Type ST1A Excitacion System. ESST1A in PSSE and PSLF

# Arguments

  * `UEL_flags::Int`: Code input for Underexcitization limiter (UEL) entry. Not supported, validation range: `(1, 3)`
  * `PSS_flags::Int`: Code input for Power System Stabilizer (PSS) or (VOS) entry, validation range: `(1, 2)`
  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, 0.1)`
  * `Vi_lim::Tuple{Float64, Float64}`: Voltage error limits (regulator input) (Vi*min, Vi*max)
  * `Tc::Float64`: First regulator denominator (lead) time constant in s, validation range: `(0, 10)`
  * `Tb::Float64`: First regulator denominator (lag) time constant in s, validation range: `(0, 20)`
  * `Tc1::Float64`: Second regulator denominator (lead) time constant in s, validation range: `(0, 10)`
  * `Tb1::Float64`: Second regulator denominator (lead) time constant in s, validation range: `(0, 20)`
  * `Ka::Float64`: Voltage regulator gain, validation range: `(50, 1000)`
  * `Ta::Float64`: Voltage regulator time constant in s, validation range: `(0, 0.5)`
  * `Va_lim::MinMax`: Limits for regulator output `(Va_min, Va_max)`
  * `Vr_lim::MinMax`: Limits for exciter output `(Vr_min, Vr_max)`
  * `Kc::Float64`: Rectifier loading factor proportional to commutating reactance, validation range: `(0, 0.3)`
  * `Kf::Float64`: Rate feedback gain, validation range: `(0, 0.3)`
  * `Tf::Float64`: Rate feedback time constant in s, validation range: `(eps(), 1.5)`
  * `K_lr::Float64`: Exciter output current limiter gain, validation range: `(0, 5)`
  * `I_lr::Float64`: Exciter output current limit reference, validation range: `(0, 5)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
Vr1: First Lead-lag state,
Vr2: Second lead-lag state,
Va: Regulator output state,
Vr3: Feedback output state
```

  * `n_states::Int`: (**Do not modify.**) ST1A has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ST1A has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
