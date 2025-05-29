```
forward_map(prior::AbstractSimulatorPrior, ζ)
```

Applies the forward map from the sample space of the prior to the parameter space of the forward model (simulator). Note that this mapping need not necessarily be bijective in the case of hierarchical or reparamterized formulations of the model parameter prior. Defaults to returning `identity(ζ)`.
