```
ising2d!(s=rand_ising2d(), β=β_ising2d, niters=10^3, rng=default_rng();
    algorithm=default_algorithm())
```

updates the 2-dimensional array `s` with values ±1 randomly by 2D Ising model rule.

Example 1:

```julia
using Ising2D
@time s = ising2d!(rand_ising2d(), β_ising2d, 10^5)
plot_ising2d(s)
```

Example 2:

```julia
using Ising2D
@time s = ising2d!(rand_ising2d(), β_ising2d, 10^5; algorithm=IfElse())
plot_ising2d(s)
```
