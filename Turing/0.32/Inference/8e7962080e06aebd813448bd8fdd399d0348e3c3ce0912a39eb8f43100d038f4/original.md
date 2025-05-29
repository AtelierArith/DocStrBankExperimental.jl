```
SMC(space...)
SMC([resampler = AdvancedPS.ResampleWithESSThreshold(), space = ()])
SMC([resampler = AdvancedPS.resample_systematic, ]threshold[, space = ()])
```

Create a sequential Monte Carlo sampler of type [`SMC`](@ref) for the variables in `space`.

If the algorithm for the resampling step is not specified explicitly, systematic resampling is performed if the estimated effective sample size per particle drops below 0.5.
