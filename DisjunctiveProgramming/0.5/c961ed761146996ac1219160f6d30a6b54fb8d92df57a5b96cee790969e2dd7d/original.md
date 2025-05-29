```
JuMP.build_variable(_error::Function, info::VariableInfo, 
                    ::Union{Type{Logical}, Logical})
```

Extend `JuMP.build_variable` to work with logical variables. This in  combination with `JuMP.add_variable` enables the use of  `@variable(model, [var_expr], Logical)`.
