```
loglikelihood(DM::DataModel, θ::AbstractVector) -> Real
```

Calculates the logarithm of the likelihood $L$, i.e. $\ell(\mathrm{data} \, | \, \theta) \coloneqq \mathrm{ln} \big( L(\mathrm{data} \, | \, \theta) \big)$ given a `DataModel` and a parameter configuration $\theta$.
