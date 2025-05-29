```
hess = hessian(expr_tree, x)
```

点 `x` での `expr_tree` のヘッセ行列を前方自動微分を用いて評価します。

例:

```julia
julia> hessian(:(x[1]^2 + x[2]), rand(2))
[2.0 0.0; 0.0 0.0]
```
