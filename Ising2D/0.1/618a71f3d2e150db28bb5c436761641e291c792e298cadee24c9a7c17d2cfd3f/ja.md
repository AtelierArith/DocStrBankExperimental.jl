```
ising2d!(::MultiFor, s=rand_ising2d(), β=β_ising2d, niters=10^3, rng=default_rng())
```

は、複数のforループを使用するアルゴリズムを使用します。

例:

```julia
s = ones_ising2d()
ising2d!(MultiFor(), s)
plot_ising2d(s)
```
