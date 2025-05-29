```
struct SteadyStateEquation <: AbstractEquation ⋯ end
```

Data structure representing an individual steady state equation.

Steady state equations can be constructed from the dynamic equations of the model. Each steady state variable has two unknowns, level and slope, so from each dynamic equation we construct two steady state equations.

Steady state equations can also be constructed with [`@steadystate`](@ref) after [`@initialize`](@ref) has been called. We call such equations steady state constraints.
