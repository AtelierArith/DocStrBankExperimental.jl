```
std_error(B::ErrorPropagator, gradient[, lvl])
```

Gives the first-order standard error estimate of a function `f` acting on the arguments of the error propagator. `gradient` is either the gradient of `f` (a function) or a vector `∇f(means(B))`. To get an estimate mean value of `f`, `mean(B, f)` can be used.
