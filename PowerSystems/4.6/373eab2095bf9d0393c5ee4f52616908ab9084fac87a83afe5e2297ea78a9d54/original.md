```
mutable struct IEEETurbineGov1 <: TurbineGov
    K::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    U0::Float64
    U_c::Float64
    valve_position_limits::MinMax
    T4::Float64
    K1::Float64
    K2::Float64
    T5::Float64
    K3::Float64
    K4::Float64
    T6::Float64
    K5::Float64
    K6::Float64
    T7::Float64
    K7::Float64
    K8::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

IEEE Type 1 Speed-Governing Model

# Arguments

  * `K::Float64`: Governor Gain, validation range: `(5, 30)`
  * `T1::Float64`: Input Filter Lag, validation range: `(0, 5)`
  * `T2::Float64`: Input Filter Lead, validation range: `(0, 10)`
  * `T3::Float64`: Valve position Time Constant, validation range: `(eps(), 1)`
  * `U0::Float64`: Maximum Valve Opening Rate, validation range: `(0.01, 0.03)`
  * `U_c::Float64`: Maximum Valve closing rate, validation range: `(-0.3, 0)`
  * `valve_position_limits::MinMax`: Valve position limits in MW
  * `T4::Float64`: Time Constant inlet steam, validation range: `(0, 1)`
  * `K1::Float64`: Fraction of high presure shaft power, validation range: `(-2, 1)`
  * `K2::Float64`: Fraction of low presure shaft power, validation range: `(0, nothing)`
  * `T5::Float64`: Time constant for second boiler pass, validation range: `(0, 10)`
  * `K3::Float64`: Fraction of high presure shaft power second boiler pass, validation range: `(0, 0.5)`
  * `K4::Float64`: Fraction of low presure shaft power second boiler pass, validation range: `(0, 0.5)`
  * `T6::Float64`: Time constant for third boiler pass, validation range: `(0, 10)`
  * `K5::Float64`: Fraction of high presure shaft power third boiler pass, validation range: `(0, 0.35)`
  * `K6::Float64`: Fraction of low presure shaft power third boiler pass, validation range: `(0, 0.55)`
  * `T7::Float64`: Time constant for fourth boiler pass, validation range: `(0, 10)`
  * `K7::Float64`: Fraction of high presure shaft power fourth boiler pass, validation range: `(0, 0.3)`
  * `K8::Float64`: Fraction of low presure shaft power fourth boiler pass, validation range: `(0, 0.3)`
  * `P_ref::Float64`: (default: `1.0`) Reference Power Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) of the IEEETurbineGov model are:

```
x_g1: First Governor integrator,
x_g2: Governor output,
x_g3: First Turbine integrator, 
x_g4: Second Turbine Integrator, 
x_g5: Third Turbine Integrator, 
x_g6: Fourth Turbine Integrator,
```

  * `n_states::Int`: (**Do not modify.**) IEEEG1 has 6 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) IEEEG1 has 6 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
