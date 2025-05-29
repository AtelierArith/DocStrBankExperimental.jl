```
indices = get_elemental_variables(expr_tree)
```

Return the `indices` of the variable appearing in `expr_tree`. This function is used to find the elemental variables from the expression tree of an element function. `expr_tree` may be an `Expr`, a `Type_expr_tree` or a `Complete_expr_tree`.

Example:

```julia
julia> get_elemental_variables(:(x[1] + x[3]) )
[1, 3]
julia> get_elemental_variables(:(x[1]^2 + x[6] + x[2]) )
[1, 6, 2]
```
