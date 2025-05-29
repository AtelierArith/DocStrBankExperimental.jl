```
mutable struct DynamicGenerator{
    M <: Machine,
    S <: Shaft,
    A <: AVR,
    TG <: TurbineGov,
    P <: PSS,
} <: DynamicInjection
    name::String
    ω_ref::Float64
    machine::M
    shaft::S
    avr::A
    prime_mover::TG
    pss::P
    base_power::Float64
    n_states::Int
    states::Vector{Symbol}
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

A dynamic generator with the necessary data for modeling the dynamic response of a generator in a phasor or electromagnetic transient simulation.

Dynamic generator is composed by 5 components, namely a [Machine](@ref), a [Shaft](@ref), an Automatic Voltage Regulator ([AVR](@ref)), a [Prime Mover and Turbine Governor](@ref "TurbineGov"), and Power System Stabilizer ([PSS](@ref)). It must be attached to a [`StaticInjection`](@ref) device using [`add_component!`](@ref add_component!(     sys::System,     dyn_injector::DynamicInjection,     static_injector::StaticInjection;     kwargs..., )), which contains all the rest of the generator's data that isn't specific to its dynamic response.

# Arguments

  * `name::String`: Name of generator.
  * `ω_ref::Float64`: Frequency reference set-point in pu.
  * `machine <: Machine`: [Machine](@ref) model for modeling the electro-magnetic phenomena.
  * `shaft <: Shaft`: [Shaft](@ref) model for modeling the electro-mechanical phenomena.
  * `avr <: AVR`: [AVR](@ref) model of the excitacion system.
  * `prime_mover <: TurbineGov`: [Prime Mover and Turbine Governor model](@ref "TurbineGov") for mechanical power.
  * `pss <: PSS`: [PSS](@ref) model.
  * `base_power::Float64`: (default: `100.0`) Base power of the unit (MVA) for [per unitization](@ref per_unit). Although this has a default, in almost all cases `base_power` should be updated to equal the `base_power` field of the [`StaticInjection`](@ref) device that this dynamic generator will be attached to.
  * `n_states::Int`: (**Do not modify.**)  Number of states (will depend on the inputs above).
  * `states::Vector{Symbol}`: (**Do not modify.**) Vector of states (will depend on the inputs above).
  * `ext::Dict{String, Any}`: (default: `Dict{String, Any}()`) An [*ext*ra dictionary](@ref additional_fields) for users to add metadata that are not used in simulation
  * `internal::InfrastructureSystemsInternal`: (**Do not modify.**) PowerSystems.jl internal reference
