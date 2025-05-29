```
ProbForwardPlanner(;
    search_noise::Float64 = 1.0,
    kwargs...
)
```

A probabilistic variant of forward best-first search. Instead of always expanding the node with lowest $f$ value in the search frontier, this samples a node to expand according to Boltzmann distribution, where the $f$ value of a frontier node is treated as the unnormalized log probability of expansion.

The temperature for Boltzmann sampling is defined by `search_noise`. Higher values lead to more random search, lower values lead to more deterministic search.

Useful for simulating a diversity of potentially sub-optimal plans, especially when paired with a limited `max_nodes` budget.

An alias for `ForwardPlanner{Float64}`. See [`ForwardPlanner`](@ref) for other arguments.
