```
constrain(pop::UncertainScalarPopulation, constraint::SamplingConstraint, n::Int = 30000)
```

Constrain an `UncertainScalarPopulation` by the given sampling `constraint`. If the  sampling constraint requires resampling to compute, resample `n` times.
