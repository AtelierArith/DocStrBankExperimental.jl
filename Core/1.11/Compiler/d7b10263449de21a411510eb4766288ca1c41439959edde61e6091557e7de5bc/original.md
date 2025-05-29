```
struct InferenceLattice{𝕃<:AbstractLattice} <: AbstractLattice
```

The full lattice used for abstract interpretation during inference. Extends a base lattice `𝕃` and adjoins `LimitedAccuracy`.
