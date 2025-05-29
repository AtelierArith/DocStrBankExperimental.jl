```
obs_distributions(hmm)
obs_distributions(hmm, control)
```

Return a vector of observation distributions, one for each state of `hmm` (possibly when `control` is applied).

These distribution objects should implement

  * `Random.rand(rng, dist)` for sampling
  * `DensityInterface.logdensityof(dist, obs)` for inference
  * `StatsAPI.fit!(dist, obs_seq, weight_seq)` for learning
