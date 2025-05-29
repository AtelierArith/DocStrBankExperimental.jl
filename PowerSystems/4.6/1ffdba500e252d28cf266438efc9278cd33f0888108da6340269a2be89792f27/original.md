```
mutable struct AndersonFouadMachine <: Machine
    R::Float64
    Xd::Float64
    Xq::Float64
    Xd_p::Float64
    Xq_p::Float64
    Xd_pp::Float64
    Xq_pp::Float64
    Td0_p::Float64
    Tq0_p::Float64
    Td0_pp::Float64
    Tq0_pp::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 6-[states](@ref S) synchronous machine: Anderson-Fouad model

# Arguments

  * `R::Float64`: Resistance after EMF in machine per unit, validation range: `(0, nothing)`
  * `Xd::Float64`: Reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq::Float64`: Reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Xd_p::Float64`: Transient reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq_p::Float64`: Transient reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Xd_pp::Float64`: Sub-Transient reactance after EMF in d-axis per unit, validation range: `(0, nothing)`
  * `Xq_pp::Float64`: Sub-Transient reactance after EMF in q-axis per unit, validation range: `(0, nothing)`
  * `Td0_p::Float64`: Time constant of transient d-axis voltage, validation range: `(0, nothing)`
  * `Tq0_p::Float64`: Time constant of transient q-axis voltage, validation range: `(0, nothing)`
  * `Td0_pp::Float64`: Time constant of sub-transient d-axis voltage, validation range: `(0, nothing)`
  * `Tq0_pp::Float64`: Time constant of sub-transient q-axis voltage, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
ψq: q-axis stator flux,
ψd: d-axis stator flux,
eq_p: q-axis transient voltage,
ed_p: d-axis transient voltage,
eq_pp: q-axis subtransient voltage,
ed_pp: d-axis subtransient voltage
```

  * `n_states::Int`: (**Do not modify.**) The states AndersonFouadMachine has 6 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
