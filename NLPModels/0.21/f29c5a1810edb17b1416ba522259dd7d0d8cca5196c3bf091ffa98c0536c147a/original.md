```
Hv = hprod(nlp, x, y, v; obj_weight=1.0)
```

Evaluate the product of the Lagrangian Hessian at `(x,y)` with the vector `v`, with objective function scaled by `obj_weight`, where the Lagrangian Hessian is

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

with `σ = obj_weight` .
