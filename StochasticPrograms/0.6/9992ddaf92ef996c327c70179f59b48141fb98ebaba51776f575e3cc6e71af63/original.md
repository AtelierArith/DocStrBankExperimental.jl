```
sample!(stochasticprogram::TwoStageStochasticProgram, sampler::AbstractSampler, n::Integer)
```

Sample `n` scenarios using `sampler` and add to the two-stage `stochasticprogram`. If the `stochasticprogram` is distributed, scenarios will be distributed evenly across workers.
