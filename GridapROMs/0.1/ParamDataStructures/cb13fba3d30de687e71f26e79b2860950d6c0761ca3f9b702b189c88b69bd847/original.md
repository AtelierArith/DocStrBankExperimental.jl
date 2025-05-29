```
abstract type TransientRealization{P<:Realization,T<:Real} <: AbstractRealization end
```

Represents temporal parametric realizations, i.e. samples extracted from a given parameter space for every time step in a temporal range. The most obvious application of this type are transient PDEs, where an initial condition is given. Following this convention, the initial time instant is kept separate from the other time steps.
