```
posterior_predictive(model, chain, n_samples::Int, f=x -> x)
```

Returns posterior predictive distribution and optionally applies function to samples      on each replication

  * `model`: the data generating function of a model
  * `chain`: an MCMCChains chain object
  * `n_samples`: the number of samples
  * `f`: a function that is applied to each sample from posterior predictive distribution
