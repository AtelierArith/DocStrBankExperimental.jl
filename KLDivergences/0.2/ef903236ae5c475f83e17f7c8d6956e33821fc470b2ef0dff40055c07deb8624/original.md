```
KL(p::Distribution, q::Distribution) -> T
KL(p::Distribution, q::Distribution, n_samples::Int) -> T
```

Return the KL divergence of  KL(p||q), either by sampling or analytically
