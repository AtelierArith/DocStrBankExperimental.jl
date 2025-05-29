```julia
mutable struct OrbitalElements{F} <: AstrodynamicalModels.AstrodynamicalState{F, 6}
```

A mutable vector, with labels, for 6DOF Keplerian states.
