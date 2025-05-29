```
constrain_box!(model::StateSpaceModel, str::String, lb::Fl, ub::Fl) where Fl
```

Map a constrained hyperparameter $\psi \in [lb, ub]$ to an unconstrained hyperparameter $\psi_* \in \mathbb{R}$.

The mapping is $\psi = lb + \frac{ub - lb}{1 + \exp(-\psi_{*})}$
