```
constrain_variance!(model::StateSpaceModel, str::String)
```

Map a constrained hyperparameter $\psi \in \mathbb{R}^+$ to an unconstrained hyperparameter $\psi_* \in \mathbb{R}$.

The mapping is $\psi = \psi_*^2$
