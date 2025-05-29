```
unconstrain_identity!(model::StateSpaceModel, str::String)
```

Map an unconstrained hyperparameter $\psi_* \in \mathbb{R}$ to a constrained hyperparameter $\psi \in \mathbb{R}$. This function is necessary to copy values from a location to another inside `HyperParameters`

The mapping is $\psi_* = \psi$
