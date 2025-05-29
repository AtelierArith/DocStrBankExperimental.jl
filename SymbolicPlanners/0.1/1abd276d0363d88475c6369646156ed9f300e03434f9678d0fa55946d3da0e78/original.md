```
MixturePolicy(policies, [weights, rng::AbstractRNG])
```

A mixture of underlying `policies` with associated `weights`. If provided, `weights` must be non-negative and sum to one. Otherwise a uniform mixture is assumed.
