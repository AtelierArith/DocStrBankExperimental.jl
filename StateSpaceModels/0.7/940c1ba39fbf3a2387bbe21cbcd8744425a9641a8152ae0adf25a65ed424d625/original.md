```
unconstrain_variance!(model::StateSpaceModel, str::String)
```

Map an unconstrained hyperparameter $\psi_{*} \in \mathbb{R}$ to a constrained hyperparameter  $\psi \in \mathbb{R}^+$.

The mapping is $\psi_{*} = \sqrt{\psi}$.
