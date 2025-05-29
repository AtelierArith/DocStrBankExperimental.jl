```
pull(instance::CombinatorialInstance{T}, arms::Vector{T}) where T
```

For the given bandit, plays the given solution (i.e. set of arms). This function returns both the reward and the regret this action caused (zero if the action is optimum, greater than zero otherwise).
