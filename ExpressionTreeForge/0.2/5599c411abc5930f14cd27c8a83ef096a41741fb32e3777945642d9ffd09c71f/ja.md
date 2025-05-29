```
gradient = gradient_forward(expr_tree, x)
```

`expr_tree`の点`x`における`gradient`を前方自動微分法で評価します。

例:

```julia
julia> gradient_forward(:(x[1] + x[2]), rand(2))
[1.0 1.0]
```
