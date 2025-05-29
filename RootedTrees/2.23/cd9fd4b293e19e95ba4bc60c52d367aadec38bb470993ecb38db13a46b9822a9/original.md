```
RungeKuttaMethod(A, b, c=vec(sum(A, dims=2)))
```

Represent a Runge-Kutta method with Butcher coefficients `A`, `b`, and `c`. If `c` is not provided, the usual "row sum" requirement of consistency with autonomous problems is applied.
