```
mutable struct ESST4B <: AVR
    Tr::Float64
    K_pr::Float64
    K_ir::Float64
    Vr_lim::MinMax
    Ta::Float64
    K_pm::Float64
    K_im::Float64
    Vm_lim::MinMax
    Kg::Float64
    Kp::Float64
    Ki::Float64
    VB_max::Float64
    Kc::Float64
    Xl::Float64
    θp::Float64
    V_ref::Float64
    θp_rad::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

In these excitation systems, voltage (and also current in compounded systems) is transformed to an appropriate level. Rectifiers, either controlled or non-controlled, provide the necessary direct current for the generator field. Parameters of IEEE Std 421.5 Type ST4B Excitacion System. ESST4B in PSSE and PSLF

# Arguments

  * `Tr::Float64`: Regulator input filter time constant in s, validation range: `(0, 0.5)`
  * `K_pr::Float64`: Regulator propotional gain, validation range: `(0, 75)`
  * `K_ir::Float64`: Regulator integral gain, validation range: `(0, 75)`
  * `Vr_lim::MinMax`: Voltage regulator limits (Vi*min, Vi*max)
  * `Ta::Float64`: Voltage regulator time constant in s, validation range: `(0, 1)`
  * `K_pm::Float64`: Voltage regulator proportional gain output, validation range: `(0, 1.2)`
  * `K_im::Float64`: Voltage regulator integral gain output, validation range: `(0, 18)`
  * `Vm_lim::MinMax`: Limits for inner loop output `(Vm_min, Vm_max)`
  * `Kg::Float64`: Feedback gain constant of the inner loop field regulator, validation range: `(0, 1.1)`
  * `Kp::Float64`: Potential circuit (voltage) gain coefficient, validation range: `(0, 10)`
  * `Ki::Float64`: Compound circuit (current) gain coefficient, validation range: `(0, 1.1)`
  * `VB_max::Float64`: Maximum available exciter voltage, validation range: `(1, 20)`
  * `Kc::Float64`: Rectifier loading factor proportional to commutating reactance, validation range: `(0, 1)`
  * `Xl::Float64`: Reactance associated with potential source, validation range: `(0, 0.5)`
  * `θp::Float64`: Potential circuit phase angle (degrees), validation range: `(-90, 90)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `θp_rad::Float64`: (default: `θp*π*inv(180)`) (**Do not modify.**) Potential circuit phase angle (radians)
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vm: Sensed terminal voltage,
Vt: Sensed Terminal Voltage,
Vr1: Regulator Integrator,
Vr2: Regulator Output,
Vm: Output integrator
```

  * `n_states::Int`: (**Do not modify.**) ST4B has 4 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) ST4B has 4 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
