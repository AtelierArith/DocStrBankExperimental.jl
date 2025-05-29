```
VariableConstrainedOnCreation <: AbstractVariable
```

変数 `scalar_variables` は `set` に属するように制約されています。

この変数を追加することは、次のように理解できます：

```julia
function JuMP.add_variable(
    model::GenericModel,
    variable::VariableConstrainedOnCreation,
    names,
)
    var_ref = add_variable(model, variable.scalar_variable, name)
    add_constraint(model, VectorConstraint(var_ref, variable.set))
    return var_ref
end
```

しかし、代わりに `MOI.add_constrained_variable(model, variable.set)` を使用して変数を追加します。
