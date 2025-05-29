```julia
formalism(
    psp::PseudoPotentialIO.AbstractPsP
) -> Union{Type{PseudoPotentialIO.NormConservingPsP}, Type{PseudoPotentialIO.ProjectorAugmentedWavePsP}, Type{PseudoPotentialIO.UltrasoftPsP}}

```

Formalism of the pseudopotential (norm-conserving, ultrasoft, projector-augmented wave, or Coulomb).

```julia
formalism(psp)
```

defined at [`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:287`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl).
