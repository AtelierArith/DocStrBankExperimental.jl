```
mutable struct ESDC1A <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
    Tb::Float64
    Tc::Float64
    Vr_lim::MinMax
    Ke::Float64
    Te::Float64
    Kf::Float64
    Tf::Float64
    switch::Int
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

Self-excited shunt fields with the voltage regulator operating in a mode commonly termed buck-boost.  Parameters of IEEE Std 421.5 Type DC1A Excitacion System. This model corresponds to ESDC1A in PSSE and PSLF

# Arguments

  * `Tr::Float64`: Voltage Measurement Time Constant in s, validation range: `(0, 0.5)`
  * `Ka::Float64`: Amplifier Gain, validation range: `(10, 500)`
  * `Ta::Float64`: Amplifier Time Constant in s, validation range: `(0, 1)`
  * `Tb::Float64`: Regulator input Time Constant in s, validation range: `(0, nothing)`
  * `Tc::Float64`: Regulator input Time Constant in s, validation range: `(0, nothing)`
  * `Vr_lim::MinMax`: Voltage regulator limits (regulator output) (Vi*min, Vi*max)
  * `Ke::Float64`: Exciter constant related to self-excited field, validation range: `(0, nothing)`
  * `Te::Float64`: Exciter time constant, integration rate associated with exciter control, validation range: `(eps(), 1)`
  * `Kf::Float64`: Excitation control system stabilizer gain, validation range: `(eps(), 0.3)`
  * `Tf::Float64`: Excitation control system stabilizer time constant, validation range: `(eps(), nothing)`
  * `switch::Int`: Switch, validation range: `(0, 1)`
  * `E_sat::Tuple{Float64, Float64}`: Exciter output voltage for saturation factor: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: Exciter saturation factor at exciter output voltage: (Se(E1), Se(E2))
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (default: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**Do not modify.**) Coefficients (A,B) of the function: Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vt: Terminal Voltage,
Vr1: input lead lag,
Vr2: Regulator Output,
Vf: Exciter Output, 
Vr3: Rate feedback integrator
```

  * `n_states::Int`: (**Do not modify.**) The ESDC1A has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ESDC1A has 5 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
