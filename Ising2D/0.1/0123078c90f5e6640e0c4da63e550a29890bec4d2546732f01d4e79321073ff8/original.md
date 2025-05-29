```
ising2d!(::IfElse, s=rand_ising2d(), β=β_ising2d, niters=10^3, rng=default_rng())
```

uses the algorithm using ifelse in only one for-loop.

Example:

```julia
s = ones_ising2d()
ising2d!(IfElse(), s)
plot_ising2d(s)
```
