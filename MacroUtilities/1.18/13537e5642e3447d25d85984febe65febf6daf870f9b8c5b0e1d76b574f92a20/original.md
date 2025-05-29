```
replace_symbols(expr, replace_values::Vector{<:Pair{Symbol, <:Any}}) -> (new_expr, was_replaced::Bool)
```

For each `x_old => x_new` in `replace_values`, recursively replace each instance of `x_old` in any argument of `expr` with `x_new`
