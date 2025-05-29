```
mutable struct DynamicInverter{
    C <: Converter,
    O <: OuterControl,
    IC <: InnerControl,
    DC <: DCSource,
    P <: FrequencyEstimator,
    F <: Filter,
} <: DynamicInjection
    name::String
    ω_ref::Float64
    converter::C
    outer_control::O
    inner_control::IC
    dc_source::DC
    freq_estimator::P
    filter::F
    limiter::Union{nothing, OutputCurrentLimiter}
    base_power::Float64
    n_states::Int
    states::Vector{Symbol}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A dynamic inverter with the necessary data for modeling the dynamic response of an inverter in a phasor or electromagnetic transient simulation.

A dynamic inverter is composed by 6 components, namely a [Converter](@ref), [Outer Loop Control](@ref OuterControl), [Inner Loop Control](@ref InnerControl), a [DC Source](@ref DCSource), a [Frequency Estimator](@ref FrequencyEstimator) and a [Filter](@ref).

It must be attached to a [`StaticInjection`](@ref) device using [`add_component!`](@ref add_component!(     sys::System,     dyn_injector::DynamicInjection,     static_injector::StaticInjection;     kwargs..., )), which contains all the rest of the generator's data that isn't specific to its dynamic response.

# Arguments

  * `name::String`: Name of inverter.
  * `ω_ref::Float64`: Frequency reference set-point in pu.
  * `converter <: Converter`: Converter model for the PWM transformation.
  * `outer_control <: OuterControl`: An [OuterControl](@ref) controller model.
  * `inner_control <: InnerControl`: An [InnerControl](@ref) controller model.
  * `dc_source <: DCSource`: [DCSource](@ref) model.
  * `freq_estimator <: FrequencyEstimator`: a [FrequencyEstimator](@ref) (typically a [PLL](@ref P)) model.
  * `filter <: Filter`: [Filter](@ref) model.
  * `limiter <: Union{nothing, OutputCurrentLimiter}`: (default: nothing) Inner Control [Current Limiter](@ref OutputCurrentLimiter) model
  * `base_power::Float64`: (default: `100.0`) Base power of the unit (MVA) for [per unitization](@ref per_unit). Although this has a default, in almost all cases `base_power` should be updated to equal the `base_power` field of the [`StaticInjection`](@ref) device that this dynamic generator will be attached to.
  * `n_states::Int`: (**Do not modify.**)  Number of states (will depend on the inputs above).
  * `states::Vector{Symbol}`: (**Do not modify.**) Vector of states (will depend on the inputs above).
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
