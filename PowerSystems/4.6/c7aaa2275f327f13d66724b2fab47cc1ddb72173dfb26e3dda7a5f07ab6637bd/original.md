```
mutable struct EXAC1 <: AVR
    Tr::Float64
    Tb::Float64
    Tc::Float64
    Ka::Float64
    Ta::Float64
    Vr_lim::MinMax
    Te::Float64
    Kf::Float64
    Tf::Float64
    Kc::Float64
    Kd::Float64
    Ke::Float64
    E_sat::Tuple{Float64, Float64}
    Se::Tuple{Float64, Float64}
    V_ref::Float64
    saturation_coeffs::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Modified ESAC1A. This excitation systems consists of an alternator main exciter feeding its output via non-controlled rectifiers. The exciter does not employ self-excitation, and the voltage regulator power is taken from a source that is not affected by external transients. Parameters of IEEE Std 421.5 Type AC1A.  EXAC1 in PSSE and PSLF

# Arguments

  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, 0.5)`
  * `Tb::Float64`: Regulator denominator (lag) time constant in s, validation range: `(0, 20)`
  * `Tc::Float64`: Regulator numerator (lead) time constant in s, validation range: `(0, 20)`
  * `Ka::Float64`: Regulator output gain, validation range: `(0, 1000)`
  * `Ta::Float64`: Regulator output time constant in s, validation range: `(0, 10)`
  * `Vr_lim::MinMax`: Limits for regulator output `(Vr_min, Vr_max)`
  * `Te::Float64`: Exciter field time constant in s, validation range: `(eps(), 2)`
  * `Kf::Float64`: Rate feedback excitation system stabilizer gain, validation range: `(0, 0.3)`
  * `Tf::Float64`: Rate feedback time constant, validation range: `(eps(), 1.5)`
  * `Kc::Float64`: Rectifier loading factor proportional to commutating reactance, validation range: `(0, 1)`
  * `Kd::Float64`: Demagnetizing factor, function of exciter alternator reactances, validation range: `(0, 1)`
  * `Ke::Float64`: Exciter field proportional constant, validation range: `(0, 1)`
  * `E_sat::Tuple{Float64, Float64}`: Exciter output voltage for saturation factor: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: Exciter saturation factor at exciter output voltage: (Se(E1), Se(E2))
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (default: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**Do not modify.**) Coefficients (A,B) of the function: Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
Vr1: Lead-lag state,
Vr2: Regulator output state,
Ve: Integrator output state,
Vr3: Feedback output state
```

  * `n_states::Int`: (**Do not modify.**) EXAC1 has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) EXAC1 has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
