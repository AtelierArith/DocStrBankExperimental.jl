```
ArblibJL(; check_analytic=false, take_prec=false, warn_on_no_convergence=false, opts=C_NULL)
```

One-dimensional adaptive Gauss-Legendre integration using rigorous error bounds and precision ball arithmetic. Generally this assumes the integrand is holomorphic or meromorphic, which is the user's responsibility to verify. The result of the integral is not guaranteed to satisfy the requested tolerances, however the result is guaranteed to be within the error estimate.

[Arblib.jl](https://github.com/kalmarek/Arblib.jl) only supports integration of univariate real- and complex-valued functions with both inplace and out-of-place forms. See their documentation for additional details the algorithm arguments and on implementing high-precision integrands. Additionally, the error estimate is included in the return value of the integral, representing a ball.
