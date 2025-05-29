```
marginalise(D::AbstractDistribution, K::AbstractMarkovKernel)
```

Computes M, the marginalization of K with respect to D, i.e.,

M(y) = ∫ K(y,x)D(x) dx
