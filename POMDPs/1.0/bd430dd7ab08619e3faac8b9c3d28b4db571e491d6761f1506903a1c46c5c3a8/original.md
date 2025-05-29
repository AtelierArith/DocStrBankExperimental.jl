```
initialstate(m::Union{POMDP,MDP})
```

Return a distribution of initial states for (PO)MDP `m`.

If it is difficult to define the probability density or mass function explicitly, consider using `POMDPModelTools.ImplicitDistribution` to define a model for sampling.
