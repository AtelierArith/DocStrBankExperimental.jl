```
admm!(x, prox_f!, prox_g!; λ=1., α=1., ϵ_abs=1e-7, ϵ_rel=1e-4, max_iter=1000)
```

Minimize an objective function $f(x) + g(x)$, where $f(x)$ and $g(x)$ can both be nonsmooth, using alternating direction method of multipliers, also known as Douglas-Rachford splitting, overwriting `x`. See also `admm`.
