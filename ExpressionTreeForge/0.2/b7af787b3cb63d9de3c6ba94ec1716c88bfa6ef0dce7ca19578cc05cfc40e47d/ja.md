```
gradient = gradient_reverse(expr_tree, x)
```

逆自動微分法を用いて、点 `x` における `expr_tree` の `gradient` を評価します。

例:

```julia
julia> gradient_reverse(:(x[1] + x[2]), rand(2))
[1.0 1.0]
```
