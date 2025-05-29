```
mutable struct PSS2C <: PSS
    input_code_1::Int
    remote_bus_control_1::Int
    input_code_2::Int
    remote_bus_control_2::Int
    M_rtf::Int
    N_rtf::Int
    Tw1::Float64
    Tw2::Float64
    T6::Float64
    Tw3::Float64
    Tw4::Float64
    T7::Float64
    Ks2::Float64
    Ks3::Float64
    T8::Float64
    T9::Float64
    Ks1::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    T10::Float64
    T11::Float64
    Vs1_lim::Tuple{Float64, Float64}
    Vs2_lim::Tuple{Float64, Float64}
    Vst_lim::Tuple{Float64, Float64}
    T12::Float64
    T13::Float64
    PSS_Hysteresis_param::Tuple{Float64, Float64}
    Xcomp::Float64
    Tcomp::Float64
    hysteresis_binary_logic::Int
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

IEEE 421.5 2016 PSS2C IEEE Dual-Input Stabilizer Model

# Arguments

  * `input_code_1::Int`: First Input Code for stabilizer, validation range: `(1, 7)`
  * `remote_bus_control_1::Int`: First Input remote bus identification [`number`](@ref ACBus) for control. `0` identifies the local bus connected to this component
  * `input_code_2::Int`: Second Input Code for stabilizer, validation range: `(1, 6)`
  * `remote_bus_control_2::Int`: Second Input remote bus identification [`number`](@ref ACBus) for control. `0` identifies the local bus connected to this component
  * `M_rtf::Int`: M parameter for ramp tracking filter, validation range: `(0, 8)`
  * `N_rtf::Int`: N parameter for ramp tracking filter, validation range: `(0, 8)`
  * `Tw1::Float64`: Time constant for first washout filter for first input, validation range: `(eps(), nothing)`
  * `Tw2::Float64`: Time constant for second washout filter for first input, validation range: `(0, nothing)`
  * `T6::Float64`: Time constant for low-pass filter for first input, validation range: `(0, nothing)`
  * `Tw3::Float64`: Time constant for first washout filter for second input, validation range: `(eps(), nothing)`
  * `Tw4::Float64`: Time constant for second washout filter for second input, validation range: `(0, nothing)`
  * `T7::Float64`: Time constant for low-pass filter for second input, validation range: `(0, nothing)`
  * `Ks2::Float64`: Gain for low-pass filter for second input, validation range: `(0, nothing)`
  * `Ks3::Float64`: Gain for second input, validation range: `(0, nothing)`
  * `T8::Float64`: Time constant for ramp tracking filter, validation range: `(0, nothing)`
  * `T9::Float64`: Time constant for ramp tracking filter, validation range: `(eps(), nothing)`
  * `Ks1::Float64`: Gain before lead-lag blocks, validation range: `(0, nothing)`
  * `T1::Float64`: Time constant for first lead-lag block, validation range: `(0, nothing)`
  * `T2::Float64`: Time constant for first lead-lag block, validation range: `(0, nothing)`
  * `T3::Float64`: Time constant for second lead-lag block, validation range: `(0, nothing)`
  * `T4::Float64`: Time constant for second lead-lag block, validation range: `(0, nothing)`
  * `T10::Float64`: Time constant for third lead-lag block, validation range: `(0, nothing)`
  * `T11::Float64`: Time constant for third lead-lag block, validation range: `(0, nothing)`
  * `Vs1_lim::Tuple{Float64, Float64}`: First input limits `(Vs1_min, Vs1_max)`
  * `Vs2_lim::Tuple{Float64, Float64}`: Second input limits `(Vs2_min, Vs2_max)`
  * `Vst_lim::Tuple{Float64, Float64}`: PSS output limits `(Vst_min, Vst_max)`
  * `T12::Float64`: Time constant for fourth lead-lag block, validation range: `(0, nothing)`
  * `T13::Float64`: Time constant for fourth lead-lag block, validation range: `(0, nothing)`
  * `PSS_Hysteresis_param::Tuple{Float64, Float64}`: PSS output hysteresis parameters `(PSSOFF, PSSON)`
  * `Xcomp::Float64`: Stator Leakage Reactance, validation range: `(0, nothing)`
  * `Tcomp::Float64`: Time measured with compensated frequency, validation range: `(eps(), nothing)`
  * `hysteresis_binary_logic::Int`: (default: `1`) Hysteresis memory variable
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) are:

```
x_p1: 1st washout 1st input, 
x_p2: 2nd washout 1st input, 
x_p3: transducer 1st input, 
x_p4: 1st washout 2nd input, 
x_p5: 2nd washout 2nd input, 
x_p6: transducer 2nd input, 
x_p7: ramp tracking filter state 1, 
x_p8: ramp tracking filter state 2, 
x_p9: ramp tracking filter state 3, 
x_p10: ramp tracking filter state 4, 
x_p11: ramp tracking filter state 5, 
x_p12: ramp tracking filter state 6, 
x_p13: ramp tracking filter state 7, 
x_p14: ramp tracking filter state 8, 
x_p15: 1st lead-lag, 
x_p16: 2nd lead-lag, 
x_p17: 3rd lead-lag, 
x_p18: 4th lead-lag, 
x_p19: washout block for compensated frequency,
```

  * `n_states::Int`: (**Do not modify.**) IEEEST has 19 states
  * `states_types::Vector{StateTypes}`: (**Do not modify.**) IEEEST has 19 [differential](@ref states_list) [states](@ref S)
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
