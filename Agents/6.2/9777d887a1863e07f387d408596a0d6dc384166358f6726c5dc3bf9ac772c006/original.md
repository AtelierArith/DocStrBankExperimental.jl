```
random_agent(model, condition; optimistic=true, alloc = false) → agent
```

Return a random agent from the model that satisfies `condition(agent) == true`. The function generates a random permutation of agent IDs and iterates through them. If no agent satisfies the condition, `nothing` is returned instead.

## Keywords

`optimistic = true` changes the algorithm used to be non-allocating but potentially more variable in performance. This should be faster if the condition is `true` for a large proportion of the population (for example if the agents are split into groups).

`alloc` can be used to employ a different fallback strategy in case the optimistic version doesn't find any agent satisfying the condition: if the filtering condition is expensive an allocating fallback can be more performant.
