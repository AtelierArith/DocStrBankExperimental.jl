`GeometricSolution`: Solution of a geometric differential equation

Contains all fields necessary to store the solution of a GeometricProblem.

### Fields

  * `t`:  time steps
  * `s`:  NamedTuple of DataSeries for each solution component
  * `step`: store every step'th time step (default: 1)
  * `nstore`: number of time steps to store
  * `offset`: offset of current time step

### Constructors

```julia
GeometricSolution(problem, step = 1)
```

The usual way to initialise a `Solution` is by passing a [`GeometricProblem`](@ref), which can for example be an [`ODEProblem`](@ref) or [`PODEProblem`](@ref). The optional parameter `step` determines the intervals for storing the solution, i.e., if `step > 1` only every `step`'th solution is actually stored.
