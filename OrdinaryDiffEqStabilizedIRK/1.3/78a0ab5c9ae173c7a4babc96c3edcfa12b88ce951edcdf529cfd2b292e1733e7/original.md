```julia
IRKC(; eigen_est = nothing)
```

Stabilized Implicit Runge Kutta method. Implicit Runge-Kutta-Chebyshev method.

### Keyword Arguments

  * `eigen_est`: function of the form   `(integrator) -> integrator.eigen_est = upper_bound`,   where `upper_bound` is an estimated upper bound on the spectral radius of the Jacobian matrix.   If `eigen_est` is not provided, `upper_bound` will be estimated using the power iteration.

## References

REF TBD
