```
solve(mme::MME,df::DataFrame;solver="default",printout_frequency=100,tolerance = 0.000001,maxiter = 5000)
```

  * Solve the mixed model equations (no marker information) without estimating variance components.

Available solvers include `default`, `Jacobi`, `Gauss-Seidel`, and `Gibbs sampler`.
