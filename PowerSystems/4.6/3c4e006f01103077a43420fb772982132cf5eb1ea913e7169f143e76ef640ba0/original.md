```
mutable struct DEGOV1 <: TurbineGov
    droop_flag::Int
    T1::Float64
    T2::Float64
    T3::Float64
    K::Float64
    T4::Float64
    T5::Float64
    T6::Float64
    Td::Float64
    T_lim::Tuple{Float64, Float64}
    R::Float64
    Te::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

Parameters Woodward Diesel Governor Model. DEGOV1 in PSSE

# Arguments

  * `droop_flag::Int`: Droop control Flag. 0 for throttle feedback and 1 for electric power feedback, validation range: `(0, 1)`
  * `T1::Float64`: Governor mechanism time constant in s, validation range: `(0, 100)`
  * `T2::Float64`: Turbine power time constant in s, validation range: `(0, 100)`
  * `T3::Float64`: Turbine exhaust temperature time constant in s, validation range: `(0, 100)`
  * `K::Float64`: Governor gain for actuator, validation range: `(0, 100)`
  * `T4::Float64`: Governor lead time constant in s, validation range: `(0, 100)`
  * `T5::Float64`: Governor lag time constant in s, validation range: `(0, 100)`
  * `T6::Float64`: Actuator time constant in s, validation range: `(0, 100)`
  * `Td::Float64`: Engine time delay in s, validation range: `(0, 100)`
  * `T_lim::Tuple{Float64, Float64}`: Operational control limits on actuator (T*min, T*max)
  * `R::Float64`: Steady state droop parameter, validation range: `(0, 100)`
  * `Te::Float64`: Power transducer time constant in s, validation range: `(0, 100)`
  * `P_ref::Float64`: (default: `1.0`) Reference Load Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the DEGOV1 model depends on the droop flag
  * `n_states::Int`: (**Do not modify.**) The number of [states](@ref S) of the DEGOV1 model depends on the droop flag
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
