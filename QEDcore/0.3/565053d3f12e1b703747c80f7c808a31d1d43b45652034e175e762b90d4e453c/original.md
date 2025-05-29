```
PhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_coords::NTuple{N,Real},
    out_coords::NTuple{M,Real},
)
```

Construct a [`PhaseSpacePoint`](@ref) from given coordinates by using the `_generate_momenta` interface.
