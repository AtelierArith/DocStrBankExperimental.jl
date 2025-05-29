```
InPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_coords::NTuple{N,Real},
)
```

Construct a [`PhaseSpacePoint`](@ref) from given coordinates by using the `_generate_momenta` interface. The result will be `<: InPhaseSpacePoint` but **not** `<: OutPhaseSpacePoint`.

!!! note
    A similar function for [`OutPhaseSpacePoint`](@ref) does not exist from coordinates, only a full [`PhaseSpacePoint`](@ref).

