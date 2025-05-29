```
initialstate(m::Game)
```

Return a distribution of initial states for POMG `m`. If it is difficult to define the probability density or mass function explicitly, consider using `POMDPModelTools.ImplicitDistribution` to define a model for sampling.
