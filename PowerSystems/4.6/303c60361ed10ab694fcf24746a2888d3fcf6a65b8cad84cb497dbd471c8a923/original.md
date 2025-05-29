```
mutable struct CSVGN1 <: DynamicInjection
    name::String
    K::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    T5::Float64
    Rmin::Float64
    Vmax::Float64
    Vmin::Float64
    CBase::Float64
    base_power::Float64
    ext::Dict{String, Any}
    R_th::Float64
    X_th::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters of static shunt compensator: CSVGN1 in PSSE

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `K::Float64`: Gain in pu ([`DEVICE_BASE`](@ref per_unit)), validation range: `(0, nothing)`
  * `T1::Float64`: Time constant in s, validation range: `(0, nothing)`
  * `T2::Float64`: Time constant in s, validation range: `(0, nothing)`
  * `T3::Float64`: Time constant in s, validation range: `(eps(), nothing)`
  * `T4::Float64`: Time constant in s, validation range: `(0, nothing)`
  * `T5::Float64`: Time constant in s, validation range: `(0, nothing)`
  * `Rmin::Float64`: Reactor minimum Mvar, validation range: `(0, nothing)`
  * `Vmax::Float64`: Maximum voltage in pu, validation range: `(0, nothing)`
  * `Vmin::Float64`: Minimum voltage in pu, validation range: `(0, nothing)`
  * `CBase::Float64`: Capacitor (MVAR), validation range: `(0, nothing)`
  * `base_power::Float64`: Base power of the unit (MVA) for [per unitization](@ref per_unit), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `R_th::Float64`: Source Thevenin resistance
  * `X_th::Float64`: Source Thevenin reactance
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
thy: thyristor,
vr1: regulator output 1,
vr2: regulator output 2
```

  * `n_states::Int`: (**Do not modify.**) CSVGN1 has 3 states
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
