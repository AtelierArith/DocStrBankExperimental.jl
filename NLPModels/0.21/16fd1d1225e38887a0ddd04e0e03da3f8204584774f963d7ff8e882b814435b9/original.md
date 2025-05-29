```
f, g = objgrad!(nls, x, g)
f, g = objgrad!(nls, x, g, Fx; recompute::Bool=true)
```

Evaluate f(x) and ∇f(x) of `nls::AbstractNLSModel` at `x`. `Fx` is overwritten with the value of the residual `F(x)`. If `recompute` is `true`, then `Fx` is updated with the residual at `x`.
