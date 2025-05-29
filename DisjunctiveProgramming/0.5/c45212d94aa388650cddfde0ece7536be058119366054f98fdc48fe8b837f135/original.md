```
JuMP.add_variable(model::Model, v::LogicalVariable, 
                  name::String = "")::LogicalVariableRef
```

Extend `JuMP.add_variable` for [`LogicalVariable`](@ref)s. This  helps enable `@variable(model, [var_expr], Logical)`.
