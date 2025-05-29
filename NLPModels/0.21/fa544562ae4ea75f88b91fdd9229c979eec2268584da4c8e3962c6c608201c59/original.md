```
vals = hess_coord!(nlp, x, vals; obj_weight=1.0)
```

Evaluate the objective Hessian at `x` in sparse coordinate format, with objective function scaled by `obj_weight`, i.e.,

$$
σ ∇²f(x),
$$

with `σ = obj_weight` , overwriting `vals`. Only the lower triangle is returned.
