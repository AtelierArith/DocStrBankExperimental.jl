```
gradient = gradient_forward(expr_tree, x)
```

Evaluate the `gradient` of `expr_tree` at the point `x` with a forward automatic differentiation method.

Example:

```julia
julia> gradient_forward(:(x[1] + x[2]), rand(2))
[1.0 1.0]
```
