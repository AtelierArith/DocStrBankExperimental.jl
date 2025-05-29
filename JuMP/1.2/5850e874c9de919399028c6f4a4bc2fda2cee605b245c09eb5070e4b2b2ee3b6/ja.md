```
check_belongs_to_model(func::AbstractJuMPScalar, model::AbstractModel)
```

関数 `func` の変数の [`owner_model`](@ref) が `model` でない場合、[`VariableNotOwned`](@ref) をスローします。

```
check_belongs_to_model(constraint::AbstractConstraint, model::AbstractModel)
```

制約 `constraint` の変数の [`owner_model`](@ref) が `model` でない場合、[`VariableNotOwned`](@ref) をスローします。
