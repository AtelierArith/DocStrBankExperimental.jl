```
mutable struct GasTG <: TurbineGov
    R::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    AT::Float64
    Kt::Float64
    V_lim::Tuple{Float64, Float64}
    D_turb::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters of Gas Turbine-Governor. GAST in PSSE and GAST_PTI in PowerWorld

# Arguments

  * `R::Float64`: Speed droop parameter, validation range: `(eps(), 0.1)`
  * `T1::Float64`: Governor time constant in s, validation range: `(eps(), 0.5)`
  * `T2::Float64`: Combustion chamber time constant, validation range: `(eps(), 0.5)`
  * `T3::Float64`: Load limit time constant (exhaust gas measurement time), validation range: `(eps(), 5)`
  * `AT::Float64`: Ambient temperature load limit, validation range: `(0, 1)`
  * `Kt::Float64`: Load limit feedback gain, validation range: `(0, 5)`
  * `V_lim::Tuple{Float64, Float64}`: Operational control limits on fuel valve opening (V*min, V*max)
  * `D_turb::Float64`: Speed damping coefficient of gas turbine rotor, validation range: `(0, 0.5)`
  * `P_ref::Float64`: (default: `1.0`) Reference Load Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the GAST model are:

```
x_g1: Fuel valve opening,
x_g2: Fuel flow,
x_g3: Exhaust temperature load
```

  * `n_states::Int`: (**Do not modify.**) GasTG has 3 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) GAST has 3 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
