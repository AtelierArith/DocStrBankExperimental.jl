```
ImmiscibleSystem(phases; reference_densities = ones(length(phases)))
ImmiscibleSystem((LiquidPhase(), VaporPhase()), reference_densities = (1000.0, 700.0))
```

Immiscible flow system: Each component exists only in a single phase, and the number of components equal the number of phases.

Set up an immiscible system for the given phases with optional reference densitites. This system is easy to specify with [Pressure](@ref) and [Saturations](@ref) as the default primary variables. Immiscible system assume that there is no mass transfer between phases and that a phase is uniform in composition.
