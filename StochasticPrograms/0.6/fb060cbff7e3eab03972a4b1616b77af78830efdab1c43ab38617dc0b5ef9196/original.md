```
upper_confidence_interval(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler; kw...)
```

Generate a confidence interval around an upper bound of the true optimum of the two-stage `stochasticmodel` at the current confidence level, over the scenario distribution induced by `sampler`, by generating and evaluating a candidate decision.

The attribute [`NumSamples`](@ref) is the size of the sampled model used to generate a candidate decision. The attribute [`NumUpperTrials`](@ref) is the number of sampled models and the attribute [`NumEvalSamples`](@ref) is the size of the evaluation models. The confidence level can be set through the [`Confidence`](@ref) attribute.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
