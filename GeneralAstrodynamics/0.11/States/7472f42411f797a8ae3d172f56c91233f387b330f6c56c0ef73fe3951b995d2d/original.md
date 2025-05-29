```julia
mutable struct Orbit{FR, F, MU, LU, TU, AU, E, var"#s233"<:GeneralAstrodynamics.States.CartesianStateWithSTM, var"#s232"<:GeneralAstrodynamics.States.ParameterVector} <: GeneralAstrodynamics.States.AbstractOrbit{FR, F, MU, LU, TU, AU, E, var"#s233"<:GeneralAstrodynamics.States.CartesianStateWithSTM, var"#s232"<:GeneralAstrodynamics.States.ParameterVector}
```

An alias for `Orbit` instances about any systems with `CartesianStateWithSTM` descriptions.
