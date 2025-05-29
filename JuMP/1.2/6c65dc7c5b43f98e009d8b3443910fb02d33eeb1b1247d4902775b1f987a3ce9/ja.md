```
VariablesConstrainedOnCreation <: AbstractVariable
```

変数 `scalar_variables` は `set` に属するように制約されています。この変数を追加することは、次のように理解できます：

```julia
function JuMP.add_variable(model::Model, variable::JuMP.VariableConstrainedOnCreation, names)
    var_ref = JuMP.add_variable(model, variable.scalar_variable, name)
    JuMP.add_constraint(model, JuMP.VectorConstraint(var_ref, variable.set))
    return var_ref
end
```

しかし、変数は `MOI.add_constrained_variable(model, variable.set)` を使用して追加されます。`MOI.add_constrained_variable` を使用して変数を追加することと、`MOI.add_variable` を使用して変数を追加し、制約を別に追加することの違いについては、[MOI ドキュメント](https://jump.dev/MathOptInterface.jl/v0.9.3/apireference/#Variables-1)を参照してください。
