```
phase_space_dimension(proc, model, layout::AbstractPhaseSpaceLayout)::Int
```

This function needs to be implemented for the phase-space layout interface. Return the dimensionality of the phase space, i.e., the number of coordinates, for a given process and model within the specified `layout`.

The phase space dimension is a crucial quantity that determines how many independent coordinates are required to describe the system of particles in the scattering process. It depends on the number of particles involved and the specific interaction model in use.

## Arguments

  * `proc`: The scattering process definition, a subtype of [`AbstractProcessDefinition`](@ref).
  * `model`: The physics model, a subtype of [`AbstractModelDefinition`](@ref).
  * `layout`: A specific phase space layout, either [`AbstractInPhaseSpaceLayout`](@ref) or   [`AbstractOutPhaseSpaceLayout`](@ref).

## Returns

  * The integer representing the number of independent phase space coordinates.

!!! note
    This function should return a compile-time constant, i.e., a number that can be inferred from the type information of the function call alone. If this is not the case, `build_momenta` and other derived functions may become very slow.

