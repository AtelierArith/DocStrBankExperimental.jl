```
Hv = hprod!(nlp, x, v, Hv; obj_weight=1.0)
```

Evaluate the product of the objective Hessian at `x` with the vector `v` in place, with objective function scaled by `obj_weight`, where the objective Hessian is

$$
σ ∇²f(x),
$$

with `σ = obj_weight` .
