```
mutable struct ESAC8B <: AVR
    Tr::Float64
    Kp::Float64
    Ki::Float64
    Kd::Float64
    Td::Float64
    Ka::Float64
    Ta::Float64
    Vr_lim::MinMax
    Te::Float64
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

Excitation System AC8B. Used to represent the Basler Digital Excitation Control System (DECS) with PID controller in PSSE.

# Arguments

  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, nothing)`
  * `Kp::Float64`: Regulator proportional PID gain, validation range: `(0, nothing)`
  * `Ki::Float64`: Regulator integral PID gain, validation range: `(0, nothing)`
  * `Kd::Float64`: Regulator derivative PID gain, validation range: `(0, nothing)`
  * `Td::Float64`: Regulator derivative PID time constant., validation range: `(0, 10)`
  * `Ka::Float64`: Regulator output gain, validation range: `(0, 1000)`
  * `Ta::Float64`: Regulator output lag time constant in s, validation range: `(0, 10)`
  * `Vr_lim::MinMax`: Limits for exciter field voltage `(Vr_min, Vr_max)`
  * `Te::Float64`: Exciter field time constant, validation range: `(eps(), 2)`
  * `Ke::Float64`: Exciter field proportional constant, validation range: `(0, 2)`
  * `E_sat::Tuple{Float64, Float64}`: Exciter output voltage for saturation factor: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: Exciter saturation factor at exciter output voltage: (Se(E1), Se(E2))
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (default: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**Do not modify.**) Coefficients (A,B) of the function: Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
x_i: Internal PI-block state,
x_d: Internal Derivative-block state,
Vr: Voltage regulator state,
Efd: Exciter output state
```

  * `n_states::Int`: (**Do not modify.**) ESAC8B has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ESAC8B has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
