```
run_sampler!(rng::AbstractRNG, sampler::RejectionSampler, n::Int)
run_sampler!(sampler::RejectionSampler, n::Int)
```

It draws `n` iid samples of the objective function of `sampler`, and at each iteration it adapts the envelop of `sampler` by adding new segments to its envelop.
