```
Hx = hess(nlp, x; obj_weight=1.0)
```

Evaluate the objective Hessian at `x` as a sparse matrix, with objective function scaled by `obj_weight`, i.e.,

$$
σ ∇²f(x),
$$

with `σ = obj_weight` . A `Symmetric` object wrapping the lower triangle is returned.
