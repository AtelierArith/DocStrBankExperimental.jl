```
mutable struct ST6B <: AVR
    OEL_Flag::Int
    Tr::Float64
    K_pa::Float64
    K_ia::Float64
    K_da::Float64
    T_da::Float64
    Va_lim::MinMax
    K_ff::Float64
    K_m::Float64
    K_ci::Float64
    K_lr::Float64
    I_lr::Float64
    Vr_lim::MinMax
    Kg::Float64
    Tg::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

In these excitation systems, voltage (and also current in compounded systems) is transformed to an appropriate level. Rectifiers, either controlled or non-controlled, provide the necessary direct current for the generator field. Parameters of IEEE Std 421.5 Type ST6B Excitacion System. ST6B in PSSE and PSLF

# Arguments

  * `OEL_Flag::Int`: OEL Flag for ST6B: 1: before HV gate, 2: after HV gate, validation range: `(0, 2)`
  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, nothing)`
  * `K_pa::Float64`: Regulator proportional gain, validation range: `(0, nothing)`
  * `K_ia::Float64`: Regulator integral gain, validation range: `(0, nothing)`
  * `K_da::Float64`: Regulator derivative gain, validation range: `(0, nothing)`
  * `T_da::Float64`: Voltage regulator derivative channel time constant in s, validation range: `(0, nothing)`
  * `Va_lim::MinMax`: Regulator output limits (Vi*min, Vi*max)
  * `K_ff::Float64`: Pre-control gain of the inner loop field regulator, validation range: `(0, nothing)`
  * `K_m::Float64`: Forward gain of the inner loop field regulator, validation range: `(0, nothing)`
  * `K_ci::Float64`: Exciter output current limit adjustment gain, validation range: `(0, nothing)`
  * `K_lr::Float64`: Exciter output current limiter gain, validation range: `(0, nothing)`
  * `I_lr::Float64`: Exciter current limiter reference, validation range: `(0, nothing)`
  * `Vr_lim::MinMax`: Voltage regulator limits (Vi*min, Vi*max)
  * `Kg::Float64`: Feedback gain constant of the inner loop field regulator, validation range: `(0, nothing)`
  * `Tg::Float64`: Feedback time constant of the inner loop field voltage regulator in s, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
x_i: Regulator Integrator,
x_d: Regulator Derivative,
Vg: Regulator Feedback
```

  * `n_states::Int`: (**Do not modify.**) ST6B has 4 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ST6B has 4 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
