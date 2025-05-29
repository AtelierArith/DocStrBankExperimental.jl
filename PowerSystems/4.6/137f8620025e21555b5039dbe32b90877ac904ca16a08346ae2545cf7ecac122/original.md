```
mutable struct PeriodicVariableSource <: DynamicInjection
    name::String
    R_th::Float64
    X_th::Float64
    internal_voltage_bias::Float64
    internal_voltage_frequencies::Vector{Float64}
    internal_voltage_coefficients::Vector{Tuple{Float64,Float64}}
    internal_angle_bias::Float64
    internal_angle_frequencies::Vector{Float64}
    internal_angle_coefficients::Vector{Tuple{Float64,Float64}}
    base_power::Float64
    states::Vector{Symbol}
    n_states::Int
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

This struct acts as an infinity bus with time varying phasor values magnitude and angle V(t) 	heta(t). Time varying functions are represented using fourier series

# Arguments

  * `name::String`: Name of the component. Components of the same type (e.g., `PowerLoad`) must have unique names, but components of different types (e.g., `PowerLoad` and `ACBus`) can have the same name
  * `R_th::Float64`: Source Thevenin resistance, validation range: `(0, nothing)`
  * `X_th::Float64`: Source Thevenin reactance, validation range: `(0, nothing)`
  * `internal_voltage_bias::Float64`: (default: `0.0`) a0 term of the Fourier Series for the voltage
  * `internal_voltage_frequencies::Vector{Float64}`: (default: `[0.0]`) Frequencies in radians/s
  * `internal_voltage_coefficients::Vector{Tuple{Float64,Float64}}`: (default: `[(0.0, 0.0)]`) Coefficients for terms n > 1. First component corresponds to sin and second component to cos
  * `internal_angle_bias::Float64`: (default: `0.0`) a0 term of the Fourier Series for the angle
  * `internal_angle_frequencies::Vector{Float64}`: (default: `[0.0]`) Frequencies in radians/s
  * `internal_angle_coefficients::Vector{Tuple{Float64,Float64}}`: (default: `[(0.0, 0.0)]`) Coefficients for terms n > 1. First component corresponds to sin and second component to cos
  * `base_power::Float64`: (default: `100.0`) Base power of the source (MVA) for [per unitization](@ref per_unit)
  * `states::Vector{Symbol}`: (**Do not modify.**) The [states](@ref S) for time, voltage and angle
  * `n_states::Int`: (**Do not modify.**) PeriodicVariableSource has 2 states
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation, such as latitude and longitude.
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
