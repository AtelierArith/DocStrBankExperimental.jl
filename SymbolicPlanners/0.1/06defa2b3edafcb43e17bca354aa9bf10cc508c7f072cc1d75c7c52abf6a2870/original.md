```
EpsilonMixturePolicy(domain, policy, epsilons, [weights, rng::AbstractRNG])
```

A mixture of epsilon-greedy policies with different `epsilons` and mixture  `weights`, specified as `Vector`s. If provided, `weights` must be non-negative and sum to one. Otherwise a uniform mixture is assumed. The `domain` is required to determine the actions available in each state.
