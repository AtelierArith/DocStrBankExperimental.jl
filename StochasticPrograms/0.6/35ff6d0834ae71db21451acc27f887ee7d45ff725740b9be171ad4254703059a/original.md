```
sample!(stochasticprogram::StochasticProgram, stage::Integer, sampler::AbstractSampler, n::Integer)
```

Sample `n` scenarios using `sampler` and add to the `stochasticprogram` at `stage`. If the `stochasticprogram` is distributed, scenarios will be distributed evenly across workers.
