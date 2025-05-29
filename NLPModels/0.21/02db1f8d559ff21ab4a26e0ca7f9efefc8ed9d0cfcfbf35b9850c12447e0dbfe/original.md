```
vals = hess_coord!(nlp, x, y, vals; obj_weight=1.0)
```

Evaluate the Lagrangian Hessian at `(x,y)` in sparse coordinate format, with objective function scaled by `obj_weight`, i.e.,

$$
∇²L(x,y) = σ ∇²f(x) + \sum_i yᵢ ∇²cᵢ(x),
$$

with `σ = obj_weight` , overwriting `vals`. Only the lower triangle is returned.
