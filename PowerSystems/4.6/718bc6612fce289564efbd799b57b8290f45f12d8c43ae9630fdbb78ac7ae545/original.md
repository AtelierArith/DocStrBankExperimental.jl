```
mutable struct RoundRotorMachine <: Machine
    R::Float64
    Td0_p::Float64
    Td0_pp::Float64
    Tq0_p::Float64
    Tq0_pp::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Xd_pp::Float64
    Xl::Float64
    Se::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    γ_d1::Float64
    γ_q1::Float64
    γ_d2::Float64
    γ_q2::Float64
    γ_qd::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 4-[states](@ref S) round-rotor synchronous machine with quadratic/exponential saturation: IEEE Std 1110 §5.3.2 (Model 2.2). GENROU or GENROE model in PSSE and PSLF

# Arguments

  * `R::Float64`: Armature resistance, validation range: `(0, nothing)`
  * `Td0_p::Float64`: Time constant of transient d-axis voltage, validation range: `(0, nothing)`
  * `Td0_pp::Float64`: Time constant of sub-transient d-axis voltage, validation range: `(0, nothing)`
  * `Tq0_p::Float64`: Time constant of transient q-axis voltage, validation range: `(0, nothing)`
  * `Tq0_pp::Float64`: Time constant of sub-transient q-axis voltage, validation range: `(0, nothing)`
  * `Xd::Float64`: Reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq::Float64`: Reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Xd_p::Float64`: Transient reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq_p::Float64`: Transient reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Xd_pp::Float64`: Sub-Transient reactance after EMF in d-axis per unit. Note: Xd*pp = Xq*pp, validation range: `(0, nothing)`
  * `Xl::Float64`: Stator leakage reactance, validation range: `(0, nothing)`
  * `Se::Tuple{Float64, Float64}`: Saturation factor at 1 and 1.2 pu flux: S(1.0) = B(|ψ_pp|-A)^2
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `γ_d1::Float64`: (**Do not modify.**) γ_d1 parameter
  * `γ_q1::Float64`: (**Do not modify.**) γ_q1 parameter
  * `γ_d2::Float64`: (**Do not modify.**) γ_d2 parameter
  * `γ_q2::Float64`: (**Do not modify.**) γ_q2 parameter
  * `γ_qd::Float64`: (**Do not modify.**) γ_qd parameter
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
eq_p: q-axis generator voltage behind the transient reactance,
ed_p: d-axis generator voltage behind the transient reactance,
ψ_kd: flux linkage in the first equivalent damping circuit in the d-axis,
ψ_kq: flux linkage in the first equivalent damping circuit in the d-axis
```

  * `n_states::Int`: (**Do not modify.**) RoundRotorMachine has 4 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
