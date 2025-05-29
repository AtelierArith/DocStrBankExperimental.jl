```
AttractorMapper(ds::DynamicalSystem, args...; kwargs...) → mapper
```

Subtypes of `AttractorMapper` are structures that map initial conditions of `ds` to attractors. The found attractors are stored inside the `mapper`, and can be obtained by calling `attractors = extract_attractors(mapper)`.

Currently available mapping methods:

  * [`AttractorsViaProximity`](@ref)
  * [`AttractorsViaRecurrences`](@ref)
  * [`AttractorsViaFeaturizing`](@ref)

All `AttractorMapper` subtypes can be used with [`basins_fractions`](@ref) or [`basins_of_attraction`](@ref).

In addition, some mappers can be called as a function of an initial condition:

```julia
label = mapper(u0)
```

and this will on the fly compute and return the label of the attractor `u0` converges at. The mappers that can do this are:

  * [`AttractorsViaProximity`](@ref)
  * [`AttractorsViaRecurrences`](@ref)
  * [`AttractorsViaFeaturizing`](@ref) with the [`GroupViaHistogram`](@ref) configuration.

See also [`StabilityMeasuresAccumulator`](@ref) that extends this interface to accelerate estimation of stability measures.

## For developers

`AttractorMapper` defines an extendable interface. A new type needs to subtype `AttractorMapper` and implement [`extract_attractors`](@ref), `id = mapper(u0)` and the internal function `Attractors.referenced_dynamical_system(mapper)`. From these, everything else in the entire rest of the library just works! If it is not possible to implement `id = mapper(u0)`, then instead extend `basins_fractions(mapper, ics)` with `ics` a vector of initial conditions.
