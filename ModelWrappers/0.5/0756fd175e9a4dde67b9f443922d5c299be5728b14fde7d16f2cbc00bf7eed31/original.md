```julia
struct Fixed{B<:ModelWrappers.Bijection} <: ModelWrappers.AbstractConstraint
```

Utility struct to help assign boundaries to parameter - keeps parameter fixed. Useful for assigning buffer values for functions of parameter.

# Fields

  * `bijection::ModelWrappers.Bijection`
