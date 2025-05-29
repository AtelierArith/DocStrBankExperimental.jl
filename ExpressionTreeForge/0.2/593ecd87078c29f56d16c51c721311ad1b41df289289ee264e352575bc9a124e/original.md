```
hess = hessian(expr_tree, x)
```

Evaluate the Hessian of `expr_tree` at the point `x` with a forward automatic differentiation.

Example:

```julia
julia> hessian(:(x[1]^2 + x[2]), rand(2))
[2.0 0.0; 0.0 0.0]
```
