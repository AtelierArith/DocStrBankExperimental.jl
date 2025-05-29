```
enable!(sampler, clock, distribution, enablingtime, currenttime, RNG)
```

Tell the sampler to start a clock.

  * `sampler::SSA{KeyType,TimeType}` - The sampler to tell.
  * `clock::KeyType` - The ID of the clock. Can be a string, integer, tuple, etc.
  * `distribution::Distributions.UnivariateDistribution`
  * `enablingtime::TimeType` - The zero time for the clock's distribution, in absolute time. Usually equal to `when`.
  * `when::TimeType` - The current time of the simulation.
  * `rng::AbstractRNG` - A random number generator.
