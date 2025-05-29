```
struct SolidStateDetector{T,SC,CT,PT,VDM} <: AbstractConfig{T}
```

Struct to describe all parts of a solid state detector, i.e. the [`Semiconductor`](@ref), a set of [`Contact`](@ref) and (optionally) [`Passive`](@ref) and virtual drift volumes.

The properties of the parts (charge densities, fixed potentials, relative permittivity of the materials) will be used as input to the calculation of [`ElectricPotential`](@ref) and  [`WeightingPotential`](@ref) in the [`Simulation`](@ref).

## Parametric types

  * `T`: Precision type.
  * `SC`: Type of the `semiconductor`.
  * `CT`: Type of the `contacts`.
  * `PT`: Type of the `passives`.
  * `VDM`: Type of the `virtual_drift_volumes`.

## Fields

  * `name::String`: Name of the detector.
  * `semiconductor::SC`: [`Semiconductor`](@ref) of the detector.
  * `contacts::CT`: Vector of [`Contact`](@ref) of the detector.
  * `passives::PT`: Vector of [`Passive`](@ref) objects, e.g. holding structures around the detector.
  * `virtual_drift_volumes::VDM`: Vector of virtual drift volumes in which the drift can be modulated   by user-defined methods for `modulate_driftvector`, e.g. [`DeadVolume`](@ref).

See also [`Semiconductor`](@ref), [`Contact`](@ref), [`Passive`](@ref) and [`DeadVolume`](@ref).
