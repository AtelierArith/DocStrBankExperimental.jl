```
SamplingContext(
        [rng::Random.AbstractRNG=Random.default_rng()],
        [sampler::AbstractSampler=SampleFromPrior()],
        [context::AbstractContext=DefaultContext()],
)
```

Create a context that allows you to sample parameters with the `sampler` when running the model. The `context` determines how the returned log density is computed when running the model.

See also: [`DefaultContext`](@ref), [`LikelihoodContext`](@ref), [`PriorContext`](@ref)
