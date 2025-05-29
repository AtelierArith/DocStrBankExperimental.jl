```julia
mutable struct Orbit{FR, F, MU, LU, TU, AU, E, S, P} <: GeneralAstrodynamics.States.AbstractOrbit{FR, F, MU, LU, TU, AU, E, S, P}
```

An orbit, described by a `StateVector`, with parameters described by a `ParameterVector`.
