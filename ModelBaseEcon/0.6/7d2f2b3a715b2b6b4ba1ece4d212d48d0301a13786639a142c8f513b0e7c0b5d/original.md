```
SteadyStateData
```

Data structure that holds information about the steady state solution of the Model. This includes a collection of [`SteadyStateVariable`](@ref)s and two collections of [`SteadyStateEquation`](@ref)s - one for the steady state equations generated from dynamic equations and another for steady state constraints created with [`@steadystate`](@ref).
