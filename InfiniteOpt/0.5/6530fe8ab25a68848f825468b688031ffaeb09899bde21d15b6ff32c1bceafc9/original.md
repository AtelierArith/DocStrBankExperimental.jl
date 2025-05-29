```
map_expression(transform::Function, 
               expr::JuMP.AbstractJuMPScalar)::JuMP.AbstractJuMPScalar
```

Map and return a new expression of `expr` where each variable is transformed  via `transform`. This can be helpful for writing user extensions.
