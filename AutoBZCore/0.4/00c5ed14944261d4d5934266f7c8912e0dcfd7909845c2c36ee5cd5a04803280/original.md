```
AutoPTR(; norm=norm, a=1.0, nmin=50, nmax=1000, n₀=6, Δn=log(10), keepmost=2, nthreads=1)
```

Periodic trapezoidal rule with automatic convergence to tolerances passed to the solver with respect to `norm` using the routine `autosymptr` from [AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl). **This algorithm is the most efficient for smooth integrands**.
