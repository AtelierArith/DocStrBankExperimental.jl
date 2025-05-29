```
mutable struct DEGOV <: TurbineGov
    T1::Float64
    T2::Float64
    T3::Float64
    K::Float64
    T4::Float64
    T5::Float64
    T6::Float64
    Td::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters Woodward Diesel Governor Model. DEGOV in PowerWorld

# Arguments

  * `T1::Float64`: Governor mechanism time constant, validation range: `(eps(), 100)`
  * `T2::Float64`: Turbine power time constant, validation range: `(eps(), 100)`
  * `T3::Float64`: Turbine exhaust temperature time constant, validation range: `(eps(), 100)`
  * `K::Float64`: Governor gain (reciprocal of droop), validation range: `(eps(), 100)`
  * `T4::Float64`: Governor lead time constant, validation range: `(eps(), 100)`
  * `T5::Float64`: Governor lag time constant, validation range: `(eps(), 100)`
  * `T6::Float64`: Actuator time constant, validation range: `(eps(), 100)`
  * `Td::Float64`: Engine time delay, validation range: `(eps(), 100)`
  * `P_ref::Float64`: (default: `1.0`) Reference Load Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the DEGOV model are:

```
x_ecb1: Electric control box 1,
x_ecb2: Electric control box 2,
x_a1: Actuator 1,
x_a2: Actuator 2,
x_a3: Actuator 3,
```

  * `n_states::Int`: (**Do not modify.**) DEGOV has 5 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) DEGOV has 5 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
