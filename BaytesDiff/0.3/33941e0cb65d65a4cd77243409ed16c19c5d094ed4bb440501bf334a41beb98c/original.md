```julia
struct DiffObjective{O<:ModelWrappers.Objective, T<:BaytesDiff.AbstractDifferentiableTune}
```

Objective struct with additional information about AD backend and configuration.

# Fields

  * `objective::ModelWrappers.Objective`: Objective as function of a parameter vector in unconstrained space.
  * `tune::BaytesDiff.AbstractDifferentiableTune`: Automatic Differentiation configurations.
