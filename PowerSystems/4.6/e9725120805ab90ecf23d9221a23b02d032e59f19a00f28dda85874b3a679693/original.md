```
mutable struct FullMachine <: Machine
    R::Float64
    R_f::Float64
    R_1d::Float64
    R_1q::Float64
    L_d::Float64
    L_q::Float64
    L_ad::Float64
    L_aq::Float64
    L_f1d::Float64
    L_ff::Float64
    L_1d::Float64
    L_1q::Float64
    ext::Dict{String, Any}
    inv_d_fluxlink::Array{Float64,2}
    inv_q_fluxlink::Array{Float64,2}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameter of a full order flux stator-rotor model without zero sequence flux in the stator.  The derivative of stator fluxes (ψd and ψq) is NOT neglected. Only one q-axis damping circuit is considered. All parameters are in machine per unit.  Refer to Chapter 3 of [Power System Stability and Control by P. Kundur](https://www.accessengineeringlibrary.com/content/book/9781260473544) or Chapter 11 of [Power System Dynamics: Stability and Control, by J. Machowski, J. Bialek and J. Bumby](https://www.wiley.com/en-us/Power+System+Dynamics%3A+Stability+and+Control%2C+3rd+Edition-p-9781119526360), for more details.  Note that the models are somewhat different (but equivalent) due to the different Park Transformation used in both books

# Arguments

  * `R::Float64`: Resistance after EMF in machine per unit, validation range: `(0, nothing)`
  * `R_f::Float64`: Field rotor winding resistance in per unit, validation range: `(0, nothing)`
  * `R_1d::Float64`:  Damping rotor winding resistance on d-axis in per unit. This value is denoted as RD in Machowski, validation range: `(0, nothing)`
  * `R_1q::Float64`: Damping rotor winding resistance on q-axis in per unit. This value is denoted as RQ in Machowski, validation range: `(0, nothing)`
  * `L_d::Float64`: Inductance of fictitious damping that represent the effect of the three-phase stator winding in the d-axis of the rotor, in per unit. This value is denoted as L*ad + L*l in Kundur (and Ld in Machowski), validation range: `(0, nothing)`
  * `L_q::Float64`: Inductance of fictitious damping that represent the effect of the three-phase stator winding in the q-axis of the rotor, in per unit. This value is denoted as L*aq + L*l in Kundur, validation range: `(0, nothing)`
  * `L_ad::Float64`: Mutual inductance between stator winding and rotor field (and damping) winding inductance on d-axis, in per unit, validation range: `(0, nothing)`
  * `L_aq::Float64`: Mutual inductance between stator winding and rotor damping winding inductance on q-axis, in per unit, validation range: `(0, nothing)`
  * `L_f1d::Float64`: Mutual inductance between rotor field winding and rotor damping winding inductance on d-axis, in per unit, validation range: `(0, nothing)`
  * `L_ff::Float64`: Field rotor winding inductance, in per unit, validation range: `(0, nothing)`
  * `L_1d::Float64`: Inductance of the d-axis rotor damping circuit, in per unit, validation range: `(0, nothing)`
  * `L_1q::Float64`: Inductance of the q-axis rotor damping circuit, in per unit, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `inv_d_fluxlink::Array{Float64,2}`: (**Do not modify.**) Equations 3.127, 3.130, 3.131 From Kundur
  * `inv_q_fluxlink::Array{Float64,2}`: (**Do not modify.**) Equations 3.128, 3.132 From Kundur
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
ψd: d-axis stator flux,
ψq: q-axis stator flux,
ψf: field rotor flux,
ψ1d: d-axis rotor damping flux,
ψ1q: q-axis rotor damping flux
```

  * `n_states::Int`: (**Do not modify.**) FullMachine has 5 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
