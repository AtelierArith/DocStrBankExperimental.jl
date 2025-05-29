```julia
mutable struct Orbit{FR, F, MU, LU, TU, AU, E, S<:Union{GeneralAstrodynamics.States.CartesianState, GeneralAstrodynamics.States.CartesianStateWithSTM, GeneralAstrodynamics.States.KeplerianState}, P<:GeneralAstrodynamics.States.R2BPParameters} <: GeneralAstrodynamics.States.AbstractOrbit{FR, F, MU, LU, TU, AU, E, S<:Union{GeneralAstrodynamics.States.CartesianState, GeneralAstrodynamics.States.CartesianStateWithSTM, GeneralAstrodynamics.States.KeplerianState}, P<:GeneralAstrodynamics.States.R2BPParameters}
```

An alias for `Orbit` instances about `R2BP` systems.
