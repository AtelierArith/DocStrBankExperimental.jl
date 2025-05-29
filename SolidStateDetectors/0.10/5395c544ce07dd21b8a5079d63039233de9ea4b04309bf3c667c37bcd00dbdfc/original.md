```
estimate_depletion_voltage(sim::Simulation{T},
    Umin::T = minimum(broadcast(c -> c.potential, sim.detector.contacts)),
    Umax::T = maximum(broadcast(c -> c.potential, sim.detector.contacts));
    contact_id::Int = determine_bias_voltage_contact_id(sim.detector),
    tolerance::AbstractFloat = 1e-1,
    verbose::Bool = true) where {T <: AbstractFloat}
```

Estimates the potential needed to fully deplete the detector in a given [`Simulation`](@ref) at the [`Contact`](@ref) with id `contact_id` by bisection method. The default `contact_id` is determined automatically via `determine_bias_voltage_contact_id(sim.detector)`. The default searching range of potentials is set by the extrema of contact potentials.

## Arguments

  * `sim::Simulation{T}`: [`Simulation`](@ref) for which the depletion voltage should be determined.
  * `Umin::T`: The minimum value of the searching range.
  * `Umax::T`: The maximum value of the searching range.

## Keywords

  * `contact_id::Int`: The `id` of the [`Contact`](@ref) at which the potential is applied.
  * `tolerance::AbstractFloat`: The acceptable accuracy of results. Default is 1e-1.
  * `verbose::Bool = true`: Activate or deactivate additional info output. Default is `true`.

## Example

```julia
using SolidStateDetectors
sim = Simulation(SSD_examples[:InvertedCoax])
calculate_electric_potential!(sim)
estimate_depletion_voltage(sim)
```

!!! note
    The accuracy of the result depends on the precision of the initial simulation.


!!! note
    This function performs two 2D or 3D field calculations, depending on `sim`.
    Thus, keep in mind that is might consume some memory.


See also [`is_depleted`](@ref).
