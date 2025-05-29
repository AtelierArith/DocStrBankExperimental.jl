```
mutable struct OneDOneQMachine <: Machine
    R::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Td0_p::Float64
    Tq0_p::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 4-[states](@ref S) synchronous machine: Simplified Marconato model  The derivative of stator fluxes (ψd and ψq) is neglected and ωψd = ψd and  ωψq = ψq is assumed (i.e. ω=1.0). This is standard when  transmission network dynamics is neglected

# Arguments

  * `R::Float64`: Resistance after EMF in machine per unit, validation range: `(0, nothing)`
  * `Xd::Float64`: Reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq::Float64`: Reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Xd_p::Float64`: Transient reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq_p::Float64`: Transient reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Td0_p::Float64`: Time constant of transient d-axis voltage, validation range: `(0, nothing)`
  * `Tq0_p::Float64`: Time constant of transient q-axis voltage, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
eq_p: q-axis transient voltage,
ed_p: d-axis transient voltage
```

  * `n_states::Int`: (**Do not modify.**) OneDOneQMachine has 2 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
