```
PhaseSpacePoint(
    proc::AbstractProcessDefinition,
    model::AbstractModelDefinition,
    psl::AbstractPhaseSpaceLayout,
    in_momenta::NTuple{N,AbstractFourMomentum},
    out_momenta::NTuple{M,AbstractFourMomentum},
)
```

Construct the phase space point from given momenta of incoming and outgoing particles regarding a given process.
