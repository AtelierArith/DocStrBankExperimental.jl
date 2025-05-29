```
Hx = hess(nlp, x, y; obj_weight=1.0)
```

Evaluate the Lagrangian Hessian at `(x,y)` as a sparse matrix, with objective function scaled by `obj_weight`, i.e.,

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

with `σ = obj_weight` . A `Symmetric` object wrapping the lower triangle is returned.
