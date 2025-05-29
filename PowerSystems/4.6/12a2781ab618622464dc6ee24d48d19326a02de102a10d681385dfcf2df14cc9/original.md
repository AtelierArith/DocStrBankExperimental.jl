```
mutable struct STAB1 <: PSS
    KT::Float64
    T::Float64
    T1T3::Float64
    T3::Float64
    T2T4::Float64
    T4::Float64
    H_lim::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Speed-Sensitive Stabilizing Model

# Arguments

  * `KT::Float64`: K/T for washout filter, validation range: `(0, nothing)`
  * `T::Float64`: Time constant for washout filter, validation range: `(0.01, nothing)`
  * `T1T3::Float64`: Time constant division T1/T3, validation range: `(0, nothing)`
  * `T3::Float64`: Time constant, validation range: `(0.01, nothing)`
  * `T2T4::Float64`: Time constant division T2/T4, validation range: `(0, nothing)`
  * `T4::Float64`: Time constant, validation range: `(0.01, nothing)`
  * `H_lim::Float64`: PSS output limit, validation range: `(0, 0.5)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
x_p1: washout filter,
x_p2: T1/T3 lead-lag block, 
x_p3: T2/T4 lead-lag block,
```

  * `n_states::Int`: (**Do not modify.**) STAB1 has 3 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) STAB1 has 3 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
