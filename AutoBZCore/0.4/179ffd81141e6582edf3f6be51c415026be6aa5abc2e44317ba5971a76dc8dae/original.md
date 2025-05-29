```
MonkhorstPack(; npt=50, syms=nothing, nthreads=1)
```

Periodic trapezoidal rule with a fixed number of k-points per dimension, `npt`, using the `PTR` rule from [AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl). `nthreads` sets the numbers of threads used to parallelize the quadrature only when the integrand is a , in which case the user must parallelize the integrand evaluations. For no threading set `nthreads=1`. **The caller should check that the integral is converged w.r.t. `npt`**.
