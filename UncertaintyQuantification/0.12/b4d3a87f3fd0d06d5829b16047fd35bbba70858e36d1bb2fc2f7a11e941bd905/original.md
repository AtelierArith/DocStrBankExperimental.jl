```
AbstractBayesianMethod
```

Subtypes are used to dispatch to the differenct MCMC methods in [`bayesianupdating`](@ref).

Subtypes are:

  * [`SingleComponentMetropolisHastings`](@ref)
  * [`TransitionalMarkovChainMonteCarlo`](@ref)
