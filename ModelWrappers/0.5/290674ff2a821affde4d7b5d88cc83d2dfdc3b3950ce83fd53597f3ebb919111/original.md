```julia
struct Tagged{A<:NamedTuple, B<:ModelWrappers.ParameterInfo}
```

Stores information for a subset of 'model' parameter.

# Fields

  * `parameter::NamedTuple`: Subset of ModelWrapper parameter names.
  * `info::ModelWrappers.ParameterInfo`: Information about subset of parameter distributions, transformations and constraints, see [`ParameterInfo`](@ref).
