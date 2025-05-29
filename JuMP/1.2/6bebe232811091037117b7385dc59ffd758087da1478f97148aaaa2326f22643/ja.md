```
VariablesConstrainedOnCreation <: AbstractVariable
```

変数のベクトル `scalar_variables` は `set` に属するように制約されています。この変数を追加することは、次のように考えることができます：

```julia
function JuMP.add_variable(model::Model, variable::JuMP.VariablesConstrainedOnCreation, names)
    var_refs = JuMP.add_variable.(model, variable.scalar_variables,
                                  JuMP.vectorize(names, variable.shape))
    JuMP.add_constraint(model, JuMP.VectorConstraint(var_refs, variable.set))
    return JuMP.reshape_vector(var_refs, variable.shape)
end
```

しかし、変数は `MOI.add_constrained_variables(model, variable.set)` を使用して追加されます。`MOI.add_constrained_variables` を使用して変数を追加することと、`MOI.add_variables` を使用して変数を追加し、制約を別に追加することの違いについては、[MOIのドキュメント](https://jump.dev/MathOptInterface.jl/v0.9.3/apireference/#Variables-1)を参照してください。
