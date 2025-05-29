```
sample!(model::ABM, n [, weight]; kwargs...)
```

Replace the agents of the `model` with a random sample of the current agents with size `n`.

Optionally, provide a `weight`: Symbol (agent field) or function (input agent out put number) to weight the sampling. This means that the higher the `weight` of the agent, the higher the probability that this agent will be chosen in the new sampling.

# Keywords

  * `replace = true` : whether sampling is performed with replacement, i.e. all agents can

be chosen more than once.

Example usage in [Wright-Fisher model of evolution](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/wright-fisher/).
