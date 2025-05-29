```
IntegralProblem(f, domain, [p=NullParameters]; kwargs...)
```

## Arguments

  * `f::AbstractIntegralFunction`: The function to integrate
  * `domain`: The domain to integrate over, e.g. `(lb, ub)`
  * `p`: Parameters to pass to the integrand

## Keywords

Additional keywords are passed directly to the solver
