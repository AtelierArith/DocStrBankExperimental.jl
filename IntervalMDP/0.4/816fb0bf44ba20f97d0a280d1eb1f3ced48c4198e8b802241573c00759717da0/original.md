```
construct_strategy_cache(mp::Union{IntervalProbabilities, IntervalMarkovProcess}, config::AbstractStrategyConfig)
```

Construct a strategy cache from a configuration for a given interval Markov process. The resuling cache type depends on the configuration and the device to store the strategy depends on the device of the Markov process.
