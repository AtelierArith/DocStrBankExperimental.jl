```
randChi²(df::Int)
```

**alias**: `randχ²`

Generate a random variable distributed as a *chi-squared* with `df`  degrees of freedom.

It uses the *Wilson–Hilferty transformation* for `df`>=20 -  see [chi-squared distribution](https://en.wikipedia.org/wiki/Chi-squared_distribution).

**Examples**

```julia
using Plots, PosDefManifold
chi=[randχ²(2) for i=1:10000]
histogram(chi) # needs Plots package. Check your plots back-end.
```
