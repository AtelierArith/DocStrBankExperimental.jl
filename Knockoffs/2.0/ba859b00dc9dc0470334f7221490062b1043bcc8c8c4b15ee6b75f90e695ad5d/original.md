```
simulate_AR1(p::Int, a=1, b=1, tol=1e-3, max_corr=1, rho=nothing)
```

Generates `p`-dimensional correlation matrix for AR(1) Gaussian process, where successive correlations are drawn from Beta(`a`,`b`) independently. If `rho` is specified, then the process is stationary with correlation `rho`.

# Source

https://github.com/amspector100/knockpy/blob/20eddb3eb60e0e82b206ec989cb936e3c3ee7939/knockpy/dgp.py#L61
