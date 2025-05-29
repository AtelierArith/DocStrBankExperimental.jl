```
gaussian_gapprox(prior::AbstractSimulatorPrior; num_prior_samples::Int=10_000, rng::Random.AbstractRNG=Random.default_rng())
```

Builds an empirical multivariate Gaussian approximation of the given `prior` distribution by computing the moments of the transformed samples.
