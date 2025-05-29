```
mutable struct SingleCageInductionMachine <: DynamicInjection
    name::String
    R_s::Float64
    R_r::Float64
    X_ls::Float64
    X_lr::Float64
    X_m::Float64
    H::Float64
    A::Float64
    B::Float64
    base_power::Float64
    ext::Dict{String, Any}
    C::Float64
    τ_ref::Float64
    B_shunt::Float64
    X_ad::Float64
    X_aq::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 5-states three-phase single cage induction machine with quadratic torque-speed relationship

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `R_s::Float64`: Armature stator resistance, validation range: `(0, nothing)`
  * `R_r::Float64`: Rotor resistance, validation range: `(0, nothing)`
  * `X_ls::Float64`: Stator Leakage Reactance, validation range: `(0, nothing)`
  * `X_lr::Float64`: Rotor Leakage Reactance, validation range: `(0, nothing)`
  * `X_m::Float64`: Stator-Rotor Mutual Reactance, validation range: `(0, nothing)`
  * `H::Float64`: Motor Inertia Constant [s], validation range: `(0, nothing)`
  * `A::Float64`: Torque-Speed Quadratic Term, validation range: `(0, 1)`
  * `B::Float64`: Torque-Speed Linear Term, validation range: `(0, 1)`
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `C::Float64`: (**Do not modify.**) Torque-Speed Constant Term
  * `τ_ref::Float64`: Reference torque parameter
  * `B_shunt::Float64`: Susceptance Initialization Corrector Term
  * `X_ad::Float64`: (**Do not modify.**) Equivalent d-axis reactance
  * `X_aq::Float64`: (**Do not modify.**) Equivalent q-axis reactance
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
ψ_qs: stator flux in the q-axis,
ψ_ds: stator flux in the d-axis,
ψ_qr: rotor flux in the q-axis,
ψ_dr: rotor flux in the d-axis, 
ωr: Rotor speed [pu],
```

  * `n_states::Int`: (**Do not modify.**) SingleCageInductionMachine has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
