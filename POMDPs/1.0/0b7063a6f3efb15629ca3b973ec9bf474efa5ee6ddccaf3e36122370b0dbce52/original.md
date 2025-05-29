```
initialobs(m::POMDP, s)
```

Return a distribution of initial observations for POMDP `m` and state `s`.

If it is difficult to define the probability density or mass function explicitly, consider using `POMDPModelTools.ImplicitDistribution` to define a model for sampling.

This function is only used in cases where the policy expects an initial observation rather than an initial belief, e.g. in a reinforcement learning setting. It is not used in a standard POMDP simulation.
