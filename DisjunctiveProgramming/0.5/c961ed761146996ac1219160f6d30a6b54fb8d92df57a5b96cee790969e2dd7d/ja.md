```
JuMP.build_variable(_error::Function, info::VariableInfo, 
                    ::Union{Type{Logical}, Logical})
```

`JuMP.build_variable`を拡張して論理変数で動作するようにします。これにより、`JuMP.add_variable`と組み合わせて`@variable(model, [var_expr], Logical)`を使用できるようになります。
