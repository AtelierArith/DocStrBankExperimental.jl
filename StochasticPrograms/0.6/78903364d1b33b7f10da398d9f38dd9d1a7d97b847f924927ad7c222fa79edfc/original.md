```
lower_confidence_interval(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler; kw...)
```

Generate a confidence interval around a lower bound on the true optimum of the two-stage `stochasticmodel` at the current confidence level, over the scenario distribution induced by `sampler`.

The attribute [`NumSamples`](@ref) is the size of the sampled models used to generate the interval and generally governs how tight it is. The attribute [`NumLowerTrials`](@ref) is the number of sampled models. The confidence level can be set through the [`Confidence`](@ref) attribute.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
