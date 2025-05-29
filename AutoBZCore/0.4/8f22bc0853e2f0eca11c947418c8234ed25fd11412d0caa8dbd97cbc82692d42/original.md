```
PTR(; npt=50, nthreads=1)
```

Periodic trapezoidal rule with a fixed number of k-points per dimension, `npt`, using the routine `ptr` from [AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl). **The caller should check that the integral is converged w.r.t. `npt`**.
