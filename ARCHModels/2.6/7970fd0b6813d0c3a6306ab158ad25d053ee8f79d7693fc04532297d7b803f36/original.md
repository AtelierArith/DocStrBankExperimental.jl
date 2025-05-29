```
simulate(am::ARCHModel; warmup=100, rng=Random.GLOBAL_RNG)
simulate(am::ARCHModel, T; warmup=100, rng=Random.GLOBAL_RNG)
simulate(spec::UnivariateVolatilitySpec, T; warmup=100, dist=StdNormal(), meanspec=NoIntercept(), rng=Random.GLOBAL_RNG)
```

Simulate a length-T time series from a UnivariateARCHModel. 	simulate(spec::MultivariateVolatilitySpec, T; warmup=100, dist=MultivariateStdNormal(), meanspec=[NoIntercept() for i = 1:d], rng=Random.GLOBAL_RNG) Simulate a length-T time series from a MultivariateARCHModel.
