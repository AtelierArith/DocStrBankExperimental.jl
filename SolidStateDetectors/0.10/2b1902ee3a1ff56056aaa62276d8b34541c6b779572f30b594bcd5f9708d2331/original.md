```
mutable struct Simulation{T <: SSDFloat, CS <: AbstractCoordinateSystem} <: AbstractSimulation{T}
```

Collection of all parts of a simulation of a [`SolidStateDetector`](@ref).

## Parametric types

  * `T`: Precision type.
  * `CS`: Coordinate system (`Cartesian` or `Cylindrical`).

## Fields

  * `config_dict::AbstractDict`: Dictionary (parsed configuration file) which initialized the simulation.
  * `input_units::NamedTuple`: Units with which the `config_dict` should be parsed.
  * `medium::NamedTuple`: Medium of the world.
  * `detector::Union{SolidStateDetector{T}, Missing}`: The [`SolidStateDetector`](@ref) of the simulation.
  * `world::World{T, 3, CS}`: The [`World`](@ref) of the simulation.
  * `q_eff_imp::Union{EffectiveChargeDensity{T}, Missing}`: Effective charge resulting from the impurites in the [`Semiconductor`](@ref) of the `detector`.
  * `imp_scale::Union{ImpurityScale{T}, Missing}`: Scale (alpha channel) of the impurity density (for depletion handling).
  * `q_eff_fix::Union{EffectiveChargeDensity{T}, Missing}`: Fixed charge resulting from fixed space charges in [`Passive`](@ref) of the `detector`.
  * `ϵ_r::Union{DielectricDistribution{T}, Missing}`: The [`DielectricDistribution`](@ref) of the simulation.
  * `point_types::Union{PointTypes{T}, Missing}`: The [`PointTypes`](@ref) of the simulation.
  * `electric_potential::Union{ElectricPotential{T}, Missing}`: The [`ElectricPotential`](@ref) of the simulation.
  * `weighting_potentials::Vector{Any}`: The [`WeightingPotential`](@ref) for each [`Contact`](@ref) of the `detector` in the simulation.
  * `electric_field::Union{ElectricField{T}, Missing}`: The [`ElectricField`](@ref) of the simulation.
