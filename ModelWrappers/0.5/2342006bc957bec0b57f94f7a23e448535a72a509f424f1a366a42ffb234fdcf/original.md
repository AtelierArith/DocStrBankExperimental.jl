```julia
struct Unconstrained{B<:ModelWrappers.Bijection} <: ModelWrappers.AbstractConstraint
```

Utility struct to help assign boundaries to parameter - keeps parameter unconstrained. Useful for assigning buffer values for functions of parameter.

# Fields

  * `bijection::ModelWrappers.Bijection`
