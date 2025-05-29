```
StationaryStrategyConfig
```

A configuration for a strategy cache that stores stationary policies. Note that the strategy is updated at each iteration of the value iteration algorithm, if a new choice is strictly better than the previous one. See [1, Section 4.3] for more details why this is necessary. See [`construct_strategy_cache`](@ref) for more details on how to construct the cache from the configuration.

[1] Forejt, Vojtěch, et al. "Automated verification techniques for probabilistic systems." Formal Methods for Eternal Networked Software Systems: 11th International School on Formal Methods for the Design of Computer, Communication and Software Systems, SFM 2011, Bertinoro, Italy, June 13-18, 2011. Advanced Lectures 11 (2011): 53-113.
