```
expr = transform_to_Expr(expr_tree)
```

Transform `expr_tree` into an `Expr`. `expr_tree` may be a `Type_expr_tree` or a `Complete_expr_tree`. **Warning**: This function return an `Expr` with variables as `MathOptInterface.VariableIndex`. In order to get an standard `Expr` use `transform_to_Expr_julia`.
