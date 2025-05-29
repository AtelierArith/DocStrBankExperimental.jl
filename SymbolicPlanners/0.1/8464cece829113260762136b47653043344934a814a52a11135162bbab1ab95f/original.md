```
BoltzmannMixturePolicy(policy, temperatures, [weights, rng::AbstractRNG])
```

A mixture of Boltzmann policies with different `temperatures` and mixture  `weights`, specified as `Vector`s. If provided, `weights` must be non-negative and sum to one. Otherwise a uniform mixture is assumed. Q-values are computed according to the underlying `policy` provided as an argument to the constructor.
