```
build_momenta(proc, model, in_psl::AbstractInPhaseSpaceLayout, in_coords::Tuple)
```

Construct the momenta of the incoming particles using the provided phase space coordinates.

This is the user-facing function that calls `_build_momenta` internally and validates the number of coordinates against the phase space dimensionality.

# Arguments

  * `proc`: The scattering process definition, subtype of [`AbstractProcessDefinition`](@ref).
  * `model`: The physics model, subtype of [`AbstractModelDefinition`](@ref).
  * `in_psl`: The incoming phase space layout, subtype of [`AbstractInPhaseSpaceLayout`](@ref).
  * `in_coords`: A tuple of phase space coordinates that parametrize the incoming particle momenta.

# Returns

  * A collection of four-momenta representing the incoming particles. Because of performance   reasons, it is recommended to return a `Tuple` of four-momenta.
