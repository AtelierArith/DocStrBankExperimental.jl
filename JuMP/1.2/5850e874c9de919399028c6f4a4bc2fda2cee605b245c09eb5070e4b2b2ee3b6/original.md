```
check_belongs_to_model(func::AbstractJuMPScalar, model::AbstractModel)
```

Throw [`VariableNotOwned`](@ref) if the [`owner_model`](@ref) of one of the variables of the function `func` is not `model`.

```
check_belongs_to_model(constraint::AbstractConstraint, model::AbstractModel)
```

Throw [`VariableNotOwned`](@ref) if the [`owner_model`](@ref) of one of the variables of the constraint `constraint` is not `model`.
