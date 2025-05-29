```
QuickMDP(gen::Function, [id]; kwargs...)
```

Construct a generative MDP model with the function `gen` and keyword arguments.

`gen` should take three arguments: a state, an action, and a random number generator. It should return a `NamedTuple` with keys `sp` for the next state and `r` for the reward.

Keywords can be static objects or functions. See the QuickPOMDPs.jl documentation for more information.
