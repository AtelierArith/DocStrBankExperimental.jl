```
evaluate_expr_tree(expr_tree::Type_expr_tree, x::AbstractVector)
evaluate_expr_tree(expr_tree::Complete_expr_tree, x::AbstractVector)
```

ベクトル `x` に対して `expr_tree` を評価します。

例:

```julia
julia> evaluate_expr_tree(:(x[1] + x[2]), ones(2))
2.
```
