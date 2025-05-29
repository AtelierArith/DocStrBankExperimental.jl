```julia
mutable struct Orbit{FR, F, MU, LU, TU, AU, E, var"#s233"<:GeneralAstrodynamics.States.KeplerianState, var"#s232"<:GeneralAstrodynamics.States.R2BPParameters} <: GeneralAstrodynamics.States.AbstractOrbit{FR, F, MU, LU, TU, AU, E, var"#s233"<:GeneralAstrodynamics.States.KeplerianState, var"#s232"<:GeneralAstrodynamics.States.R2BPParameters}
```

An alias for `Orbit` instances about `R2BP` systems with `KeplerianState` descriptions.
