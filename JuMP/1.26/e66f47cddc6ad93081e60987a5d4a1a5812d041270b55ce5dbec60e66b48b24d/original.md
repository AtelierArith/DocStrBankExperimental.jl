```
abstract type AbstractConstraint
```

An abstract base type for all constraint types. `AbstractConstraint`s store the function and set directly, unlike [`ConstraintRef`](@ref)s that are merely references to constraints stored in a model. `AbstractConstraint`s do not need to be attached to a model.
