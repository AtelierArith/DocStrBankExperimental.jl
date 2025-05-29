```julia
struct ParameterInfo{R<:ModelWrappers.ReConstructor, U<:ModelWrappers.ReConstructor, T<:ModelWrappers.TransformConstructor}
```

Contains information about parameter distributions, transformations and constraints.

# Fields

  * `reconstruct::ModelWrappers.ReConstructor`: Contains information for flatten/unflatten parameter
  * `reconstructᵤ::ModelWrappers.ReConstructor`: Contains information to reconstruct unconstrained parameter - important for non-bijective transformations
  * `transform::ModelWrappers.TransformConstructor`: Contains information for constraining and unconstraining parameter.
