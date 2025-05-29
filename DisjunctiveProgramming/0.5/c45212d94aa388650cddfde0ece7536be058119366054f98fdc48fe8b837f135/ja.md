```
JuMP.add_variable(model::Model, v::LogicalVariable, 
                  name::String = "")::LogicalVariableRef
```

[`LogicalVariable`](@ref)のために`JuMP.add_variable`を拡張します。これにより、`@variable(model, [var_expr], Logical)`が可能になります。
