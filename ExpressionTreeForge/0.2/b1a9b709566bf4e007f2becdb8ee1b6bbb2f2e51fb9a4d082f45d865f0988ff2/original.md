```
evaluate_expr_tree(expr_tree::Type_expr_tree, x::AbstractVector)
evaluate_expr_tree(expr_tree::Complete_expr_tree, x::AbstractVector)
```

Evaluate the `expr_tree` given the vector `x`.

Example:

```julia
julia> evaluate_expr_tree(:(x[1] + x[2]), ones(2))
2.
```
