```
RosenbrockMethod(γ, A, b, c=vec(sum(A, dims=2)))
```

Represent a Rosenbrock (or Rosenbrock-Wanner, ROW) method with coefficients `γ`, `A`, `b`, and `c`. If `c` is not provided, the usual "row sum" requirement of consistency with autonomous problems is applied.

# Reference

  * Ernst Hairer, Gerhard Wanner. Solving ordinary differential equations II: Stiff and differential-algebraic problems. Springer, 2010. Section IV.7
