```
OutPhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    out_momenta::NTuple{N,AbstractFourMomentum},
)
```

Construct a [`PhaseSpacePoint`](@ref) with only output particles from given momenta. The result will be `<: OutPhaseSpacePoint` but **not** `<: InPhaseSpacePoint`.
