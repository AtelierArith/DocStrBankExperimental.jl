```
DPM(rng::AbstractRNG, N; K0 = 1, a0 = 2.0, b0 = 4.0)
```

Initialize a generic DPM with `N` observations, `K0` initial clusters and a  `Gamma(a0, b0)` prior distribution for the DP mass parameter.
