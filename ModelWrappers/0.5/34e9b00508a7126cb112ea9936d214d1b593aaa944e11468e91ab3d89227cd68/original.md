```julia
struct Constrained{B<:ModelWrappers.Bijection} <: ModelWrappers.AbstractConstraint
```

Utility struct to help assign boundaries to parameter - keeps scalar parameter constrained.

# Fields

  * `bijection::ModelWrappers.Bijection`
