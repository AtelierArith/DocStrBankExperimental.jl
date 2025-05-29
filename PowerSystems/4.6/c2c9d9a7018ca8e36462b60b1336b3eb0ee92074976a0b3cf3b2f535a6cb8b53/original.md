```
mutable struct AVRTypeI <: AVR
    Ka::Float64
    Ke::Float64
    Kf::Float64
    Ta::Float64
    Te::Float64
    Tf::Float64
    Tr::Float64
    Va_lim::MinMax
    Ae::Float64
    Be::Float64
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

Parameters of an Automatic Voltage Regulator Type I - Resembles IEEE Type DC1

# Arguments

  * `Ka::Float64`: Amplifier Gain, validation range: `(0, nothing)`
  * `Ke::Float64`: Field circuit integral deviation, validation range: `(0, nothing)`
  * `Kf::Float64`: Stabilizer Gain in s * pu/pu, validation range: `(0, nothing)`
  * `Ta::Float64`: Amplifier Time Constant in s, validation range: `(0, nothing)`
  * `Te::Float64`: Field Circuit Time Constant in s, validation range: `(0, nothing)`
  * `Tf::Float64`: Stabilizer Time Constant in s, validation range: `(0, nothing)`
  * `Tr::Float64`: Voltage Measurement Time Constant in s, validation range: `(0, nothing)`
  * `Va_lim::MinMax`: Limits for pi controler `(Va_min, Va_max)`
  * `Ae::Float64`: 1st ceiling coefficient, validation range: `(0, nothing)`
  * `Be::Float64`: 2nd ceiling coefficient, validation range: `(0, nothing)`
  * `V_ref::Float64`: (default: `1.0`) Reference Voltage Set-point (pu), validation range: `(0, nothing)`
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
Vf: Voltage field,
Vr1: Amplifier State,
Vr2: Stabilizing Feedback State,
Vm: Measured voltage
```

  * `n_states::Int`: (**Do not modify.**) The AVR Type I has 4 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) AVR Type I has 4 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
