```
mutable struct FiveMassShaft <: Shaft
    H::Float64
    H_hp::Float64
    H_ip::Float64
    H_lp::Float64
    H_ex::Float64
    D::Float64
    D_hp::Float64
    D_ip::Float64
    D_lp::Float64
    D_ex::Float64
    D_12::Float64
    D_23::Float64
    D_34::Float64
    D_45::Float64
    K_hp::Float64
    K_ip::Float64
    K_lp::Float64
    K_ex::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of 5 mass-spring shaft model.  It contains a High-Pressure (HP) steam turbine, Intermediate-Pressure (IP)  steam turbine, Low-Pressure (LP) steam turbine, the Rotor and an Exciter (EX) mover

# Arguments

  * `H::Float64`: Rotor inertia constant in MWs/MVA, validation range: `(0, nothing)`
  * `H_hp::Float64`: High pressure turbine inertia constant in MWs/MVA, validation range: `(0, nothing)`
  * `H_ip::Float64`: Intermediate pressure turbine inertia constant in MWs/MVA, validation range: `(0, nothing)`
  * `H_lp::Float64`: Low pressure turbine inertia constant in MWs/MVA, validation range: `(0, nothing)`
  * `H_ex::Float64`:  Exciter inertia constant in MWs/MVA, validation range: `(0, nothing)`
  * `D::Float64`: Rotor natural damping in pu, validation range: `(0, nothing)`
  * `D_hp::Float64`: High pressure turbine natural damping in pu, validation range: `(0, nothing)`
  * `D_ip::Float64`: Intermediate pressure turbine natural damping in pu, validation range: `(0, nothing)`
  * `D_lp::Float64`: Low pressure turbine natural damping in pu, validation range: `(0, nothing)`
  * `D_ex::Float64`: Exciter natural damping in pu, validation range: `(0, nothing)`
  * `D_12::Float64`: High-Intermediate pressure turbine damping, validation range: `(0, nothing)`
  * `D_23::Float64`: Intermediate-Low pressure turbine damping, validation range: `(0, nothing)`
  * `D_34::Float64`: Low pressure turbine-Rotor damping, validation range: `(0, nothing)`
  * `D_45::Float64`: Rotor-Exciter damping, validation range: `(0, nothing)`
  * `K_hp::Float64`: High pressure turbine angle coefficient, validation range: `(0, nothing)`
  * `K_ip::Float64`: Intermediate pressure turbine angle coefficient, validation range: `(0, nothing)`
  * `K_lp::Float64`: Low pressure turbine angle coefficient, validation range: `(0, nothing)`
  * `K_ex::Float64`: Exciter angle coefficient, validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
δ: rotor angle,
ω: rotor speed,
δ_hp: rotor angle of high pressure turbine,
ω_hp: rotor speed of high pressure turbine,
δ_ip: rotor angle of intermediate pressure turbine,
ω_ip: rotor speed of intermediate pressure turbine,
δ_lp: rotor angle of low pressure turbine,
ω_lp: rotor speed of low pressure turbine,
δ_ex: rotor angle of exciter,
ω_lp: rotor speed of exciter
```

  * `n_states::Int`: (**Do not modify.**) FiveMassShaft has 10 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
