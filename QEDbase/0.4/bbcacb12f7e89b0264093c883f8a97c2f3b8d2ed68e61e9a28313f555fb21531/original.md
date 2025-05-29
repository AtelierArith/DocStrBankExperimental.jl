```
build_momenta(proc::AbstractProcessDefinition, model::AbstractModelDefinition, in_psl::AbstractInPhaseSpaceLayout, in_coords::Real)
```

A scalar version of `build_momenta` for incoming phase space layouts (`in_psl`), where the phase space coordinates are provided as a single scalar instead of a tuple.

## Arguments:

  * `proc`: The scattering process definition, subtype of [`AbstractProcessDefinition`](@ref).
  * `model`: The physics model, subtype of [`AbstractModelDefinition`](@ref).
  * `in_psl`: The incoming phase space layout, subtype of [`AbstractInPhaseSpaceLayout`](@ref).
  * `in_coords::Real`: A single scalar representing the phase space coordinate for the   incoming particles.

## Returns:

  * A collection of four-momenta representing the incoming particles. For performance   reasons, it is recommended to return a `Tuple` of four-momenta.

## Notes:

This function is a convenience wrapper around `build_momenta`, automatically converting the scalar `in_coords` into a 1-tuple. It is useful when the incoming phase space only requires a single coordinate to define the particle momenta.
