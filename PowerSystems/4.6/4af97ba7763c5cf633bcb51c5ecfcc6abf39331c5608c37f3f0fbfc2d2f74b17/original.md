```
mutable struct ESAC6A <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
    Tk::Float64
    Tb::Float64
    Tc::Float64
    Va_lim::MinMax
    Vr_lim::MinMax
    Te::Float64
    VFE_lim::Float64
    Kh::Float64
    VH_max::Float64
    Th::Float64
    Tj::Float64
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

Modified AC6A. Used to represent field-controlled alternator-rectifier excitation systems with system-supplied electronic voltage regulators.  Parameters of IEEE Std 421.5 Type AC6A Excitacion System. ESAC6A in PSSE and PSLF

# Arguments

  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, 0.5)`
  * `Ka::Float64`: Regulator output gain, validation range: `(0, 1000)`
  * `Ta::Float64`: Regulator output lag time constant in s, validation range: `(0, 10)`
  * `Tk::Float64`: Voltage Regulator lead time constant, validation range: `(0, 10)`
  * `Tb::Float64`: Regulator denominator (lag) time constant in s, validation range: `(0, 20)`
  * `Tc::Float64`: Regulator numerator (lead) time constant in s, validation range: `(0, 20)`
  * `Va_lim::MinMax`: Limits for regulator output `(Va_min, Va_max)`
  * `Vr_lim::MinMax`: Limits for exciter field voltage `(Vr_min, Vr_max)`
  * `Te::Float64`: Exciter field time constant, validation range: `(eps(), 2)`
  * `VFE_lim::Float64`: Exciter field current limiter reference, validation range: `(-5, 20)`
  * `Kh::Float64`: Exciter field current regulator feedback gain, validation range: `(0, 100)`
  * `VH_max::Float64`: Exciter field current limiter maximum output, validation range: `(0, 100)`
  * `Th::Float64`: Exciter field current limiter denominator (lag) time constant, validation range: `(0, 1)`
  * `Tj::Float64`: Exciter field current limiter numerator (lead) time constant, validation range: `(0, 1)`
  * `Kc::Float64`: Rectifier loading factor proportional to commutating reactance, validation range: `(0, 1)`
  * `Kd::Float64`: Demagnetizing factor, function of exciter alternator reactances, validation range: `(0, 2)`
  * `Ke::Float64`: Exciter field proportional constant, validation range: `(0, 2)`
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

  * `n_states::Int`: (**Do not modify.**) ESAC6A has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ESAC6A has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
