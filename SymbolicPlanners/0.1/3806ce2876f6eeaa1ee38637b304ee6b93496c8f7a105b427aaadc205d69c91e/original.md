```
EpsilonGreedyPolicy(domain, policy, epsilon, [rng::AbstractRNG])
```

Policy that acts uniformly at random with `epsilon` chance, but otherwise  selects the best action(s) according the underlying `policy`. If there is more than one best action, tie-breaking occurs randomly. The `domain` has to be provided to determine the actions available in each state.
