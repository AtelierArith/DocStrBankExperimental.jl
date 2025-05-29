```
InPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_momenta::NTuple{N,AbstractFourMomentum},
)
```

Construct a [`PhaseSpacePoint`](@ref) with only input particles from given momenta. The result will be `<: InPhaseSpacePoint` but **not** `<: OutPhaseSpacePoint`.
