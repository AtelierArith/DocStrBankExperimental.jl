```
f = obj(nls, x)
f = obj(nls, x, Fx; recompute::Bool=true)
```

Evaluate `f(x)`, the objective function of `nls::AbstractNLSModel`. `Fx` is overwritten with the value of the residual `F(x)`. If `recompute` is `true`, then `Fx` is updated with the residual at `x`.
