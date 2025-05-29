```
mutable struct IEEEST <: PSS
    input_code::Int
    remote_bus_control::Int
    A1::Float64
    A2::Float64
    A3::Float64
    A4::Float64
    A5::Float64
    A6::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    T5::Float64
    T6::Float64
    Ks::Float64
    Ls_lim::Tuple{Float64, Float64}
    Vcu::Float64
    Vcl::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

IEEE Stabilizing Model PSS. 

# Arguments

  * `input_code::Int`: Code input for stabilizer, validation range: `(1, 6)`
  * `remote_bus_control::Int`: ACBus identification [`number`](@ref ACBus) for control. `0` identifies the bus connected to this component
  * `A1::Float64`: Filter coefficient, validation range: `(0, nothing)`
  * `A2::Float64`: Filter coefficient, validation range: `(0, nothing)`
  * `A3::Float64`: Filter coefficient, validation range: `(0, nothing)`
  * `A4::Float64`: Filter coefficient, validation range: `(0, nothing)`
  * `A5::Float64`: Filter coefficient, validation range: `(0, nothing)`
  * `A6::Float64`: Filter coefficient, validation range: `(0, nothing)`
  * `T1::Float64`: Time constant, validation range: `(0, 10)`
  * `T2::Float64`: Time constant, validation range: `(0, 10)`
  * `T3::Float64`: Time constant, validation range: `(0, 10)`
  * `T4::Float64`: Time constant, validation range: `(0, 10)`
  * `T5::Float64`: Time constant, validation range: `(0, 10)`
  * `T6::Float64`: Time constant, validation range: `(eps(), 2.0)`
  * `Ks::Float64`: Proportional gain, validation range: `(0, nothing)`
  * `Ls_lim::Tuple{Float64, Float64}`: PSS output limits for regulator output `(Ls_min, Ls_max)`
  * `Vcu::Float64`: Cutoff limiter upper bound, validation range: `(0, 1.25)`
  * `Vcl::Float64`: Cutoff limiter lower bound, validation range: `(0, 1.0)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
x_p1: 1st filter integration,
x_p2: 2nd filter integration, 
x_p3: 3rd filter integration, 
x_p4: 4rd filter integration, 
x_p5: T1/T2 lead-lag integrator, 
x_p6: T3/T4 lead-lag integrator, 
:x_p7 last integer,
```

  * `n_states::Int`: (**Do not modify.**) IEEEST has 7 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) IEEEST has 7 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
