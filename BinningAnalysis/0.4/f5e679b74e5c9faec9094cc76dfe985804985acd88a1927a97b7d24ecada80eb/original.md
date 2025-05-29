```
var(ep::ErrorPropagator, gradient[, lvl])
```

Gives the first-order variance estimate of a function `f` acting on the arguments of the error propagator. `gradient` is either the gradient of `f` (a function) or a vector `∇f(means(ep))`. To get an estimate mean value of `f`, `mean(ep, f)` can be used.
