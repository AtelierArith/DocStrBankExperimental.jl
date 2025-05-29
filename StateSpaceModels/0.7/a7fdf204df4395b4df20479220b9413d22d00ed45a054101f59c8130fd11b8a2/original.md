```
unconstrain_box!(model::StateSpaceModel, str::String, lb::Fl, ub::Fl) where Fl
```

Map an unconstrained hyperparameter $\psi_* \in \mathbb{R}$ to a constrained hyperparameter $\psi \in [lb, ub]$.

The mapping is $\psi_* = -\ln \frac{ub - lb}{\psi - lb} - 1$
