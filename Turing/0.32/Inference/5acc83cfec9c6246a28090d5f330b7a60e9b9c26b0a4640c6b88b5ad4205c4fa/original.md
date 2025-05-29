```
PG(n, space...)
PG(n, [resampler = AdvancedPS.ResampleWithESSThreshold(), space = ()])
PG(n, [resampler = AdvancedPS.resample_systematic, ]threshold[, space = ()])
```

Create a Particle Gibbs sampler of type [`PG`](@ref) with `n` particles for the variables in `space`.

If the algorithm for the resampling step is not specified explicitly, systematic resampling is performed if the estimated effective sample size per particle drops below 0.5.
