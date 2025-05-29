```
samplePosterior(hyperparameters, priorparameters, SigmaU, X, T, Y)
```

Draw samples from the posterior given the observed data. Params: 

  * `hyperparams::`[`HyperParameters`](@ref)
  * `priorparams::`[`PriorParameters`](@ref)
  * `SigmaU::`[`ConfounderStructure`](@ref)
  * `X::`[`Covariates`](@ref)
  * `T::`[`Treatment`](@ref)
  * `Y::`[`Outcome`](@ref)

Posterior samples are returned as a Vector of Gen choicemaps.
