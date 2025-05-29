```
build_momenta(proc, model, Ptot::AbstractFourMomentum, out_psl::AbstractOutPhaseSpaceLayout, out_coords::Tuple)
```

Construct the momenta of the outgoing particles using the provided phase space coordinates (`out_coords`) and total incoming momentum (`Ptot`).

This function ensures that the outgoing momenta satisfy energy and momentum conservation, consistent with the physics model in use.

# Arguments

  * `proc`: The scattering process definition, subtype of [`AbstractProcessDefinition`](@ref).
  * `model`: The physics model, subtype of [`AbstractModelDefinition`](@ref).
  * `in_moms`: The incoming four-momenta, used to compute the outgoing momenta.
  * `out_psl`: The outgoing phase space layout, subtype of [`AbstractOutPhaseSpaceLayout](@ref).
  * `out_coords`: A tuple of phase space coordinates that parametrize the outgoing particle momenta.

# Returns

  * A collection of four-momenta representing the incoming particles. Because of performance   reasons, it is recommened to return a `Tuple` of four-momenta.
