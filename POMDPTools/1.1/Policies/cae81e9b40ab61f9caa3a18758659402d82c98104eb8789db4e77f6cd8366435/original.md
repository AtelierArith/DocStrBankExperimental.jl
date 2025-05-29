```
ExplorationPolicy <: Policy
```

An abstract type for exploration policies. Sampling from an exploration policy is done using `action(exploration_policy, on_policy, k, state)`. `k` is a value that is used to determine the exploration parameter. It is usually a training step in a TD-learning algorithm.
