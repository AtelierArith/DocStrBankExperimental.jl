```
ising2d!(::MultiFor, s=rand_ising2d(), β=β_ising2d, niters=10^3, rng=default_rng())
```

uses the algorithm using multiple for-loops.

Example:

```julia
s = ones_ising2d()
ising2d!(MultiFor(), s)
plot_ising2d(s)
```
