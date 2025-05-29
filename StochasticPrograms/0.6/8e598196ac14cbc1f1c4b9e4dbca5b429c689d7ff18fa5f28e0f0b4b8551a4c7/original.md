```
confidence_interval(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

Generate a confidence interval around the true optimum of the two-stage `stochasticmodel` at level `confidence` using SAA, over the scenario distribution induced by `sampler`.

The attribute [`NumSamples`](@ref) is the size of the sampled models used to generate the interval and generally governs how tight it is. The attribute [`NumLowerTrials`](@ref) is the number of sampled models used in the lower bound calculation and the attribute [`NumUpperTrials`](@ref) is the number of sampled models used in the upper bound calculation. The attribute [`NumEvalSamples`](@ref) is the size of the sampled models used in the upper bound calculation. The confidence level can be set through the [`Confidence`](@ref) attribute.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
