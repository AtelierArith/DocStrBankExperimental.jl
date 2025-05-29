```julia
mutable struct Orbit{FR, F, MU, LU, TU, AU, E, var"#s233"<:(Union{var"#s233", var"#s232"} where {var"#s233"<:GeneralAstrodynamics.States.CartesianState, var"#s232"<:GeneralAstrodynamics.States.CartesianStateWithSTM}), var"#s232"<:GeneralAstrodynamics.States.R2BPParameters} <: GeneralAstrodynamics.States.AbstractOrbit{FR, F, MU, LU, TU, AU, E, var"#s233"<:(Union{var"#s233", var"#s232"} where {var"#s233"<:GeneralAstrodynamics.States.CartesianState, var"#s232"<:GeneralAstrodynamics.States.CartesianStateWithSTM}), var"#s232"<:GeneralAstrodynamics.States.R2BPParameters}
```

An alias for `Orbit` instances about `R2BP` systems with `CartesianState` descriptions.
