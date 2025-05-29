```
G, Gn = plr(d::AbstractIdData,na,nb,nc; initial_order = 20)
```

Perform pseudo-linear regression to estimate a model on the form `Ay = Bu + Cw` The residual sequence is estimated by first estimating a high-order arx model, whereafter the estimated residual sequence is included in a second estimation problem. The return values are the estimated system model, and the estimated noise model. `G` and `Gn` will always have the same denominator polynomial.

`armax` is an alias for `plr`. See also [`pem`](@ref), [`ar`](@ref), [`arx`](@ref) and [`arxar`](@ref)
