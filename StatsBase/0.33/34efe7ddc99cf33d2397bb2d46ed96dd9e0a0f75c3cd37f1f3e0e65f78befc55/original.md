```
kldivergence(p, q, [b])
```

Compute the Kullback-Leibler divergence from `q` to `p`, also called the relative entropy of `p` with respect to `q`, that is the sum `pᵢ * log(pᵢ / qᵢ)`. Optionally a real number `b` can be specified such that the divergence is scaled by `1/log(b)`.
