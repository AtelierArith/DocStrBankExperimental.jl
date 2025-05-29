```
mutable struct EXPIC1 <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
    Va_lim::MinMax
    Ta_2::Float64
    Ta_3::Float64
    Ta_4::Float64
    Vr_lim::MinMax
    Kf::Float64
    Tf_1::Float64
    Tf_2::Float64
    Efd_lim::MinMax
    Ke::Float64
    Te::Float64
    E_sat::Tuple{Float64, Float64}
    Se::Tuple{Float64, Float64}
    Kp::Float64
    Ki::Float64
    Kc::Float64
    V_ref::Float64
    saturation_coeffs::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Generic Proportional/Integral Excitation System

# Arguments

  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, 0.5)`
  * `Ka::Float64`: Voltage regulator gain, validation range: `(1, 500)`
  * `Ta::Float64`: Voltage regulator time constant in s, validation range: `(0, 10)`
  * `Va_lim::MinMax`: Limits for pi controler `(Vr_min, Vr_max)`
  * `Ta_2::Float64`: Voltage regulator time constant in s, validation range: `(0, nothing)`
  * `Ta_3::Float64`: Voltage regulator time constant in s, validation range: `(0, nothing)`
  * `Ta_4::Float64`: Voltage regulator time constant in s, validation range: `(0, nothing)`
  * `Vr_lim::MinMax`: Voltage regulator limits (regulator output) (Vi*min, Vi*max)
  * `Kf::Float64`: Rate feedback gain, validation range: `(0, 0.3)`
  * `Tf_1::Float64`: Rate Feedback time constant in s, validation range: `(eps(), 15)`
  * `Tf_2::Float64`: Rate Feedback time constant in s, validation range: `(0, 5)`
  * `Efd_lim::MinMax`: Field Voltage regulator limits (regulator output) (Efd*min, Efd*max)
  * `Ke::Float64`: Exciter constant, validation range: `(0, 1)`
  * `Te::Float64`: Exciter time constant, validation range: `(0, 2)`
  * `E_sat::Tuple{Float64, Float64}`: Exciter output voltage for saturation factor: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: Exciter saturation factor at exciter output voltage: (Se(E1), Se(E2))
  * `Kp::Float64`: Potential source gain, validation range: `(0, 5)`
  * `Ki::Float64`: current source gain, validation range: `(0, 1.1)`
  * `Kc::Float64`: Exciter regulation factor, validation range: `(0, 2)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (default: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**Do not modify.**) Coefficients (A,B) of the function: Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
Vr1: First Lead-lag state,
Vr2: Second regulator lead-lag state,
Vr2: Third regulator lead-lag state 
Vf: Exciter output 
Vr3: First feedback integrator,
Vr4: second feedback integrator
```

  * `n_states::Int`: (**Do not modify.**) EXPIC1 has 6 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) EXPIC has 6 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
