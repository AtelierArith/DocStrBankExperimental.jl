```
transition(m::Game, state, action)
```

Return the transition distribution from the current state-joint-action pair. If it is difficult to define the probability density or mass function explicitly, consider using `POMDPModelTools.ImplicitDistribution` to define a generative model.
