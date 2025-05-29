```julia
struct ReConstructor{F<:ModelWrappers.FlattenDefault, S<:ModelWrappers.FlattenConstructor, T<:ModelWrappers.UnflattenConstructor}
```

Contains information for flatten/unflatten construct.

# Fields

  * `default::ModelWrappers.FlattenDefault`
  * `flatten::ModelWrappers.FlattenConstructor`
  * `unflatten::ModelWrappers.UnflattenConstructor`
