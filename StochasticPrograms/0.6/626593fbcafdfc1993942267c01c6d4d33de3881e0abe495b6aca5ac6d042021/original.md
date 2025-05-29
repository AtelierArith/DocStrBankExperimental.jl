```
upper_confidence_interval(stochasticmodel::StochasticModel{2}, decision::AbstractVector, sampler::AbstractSampler; kw...)
```

Generate a confidence interval around an upper bound of the expected value of `decision` in the two-stage `stochasticmodel` at the current confidence level, over the scenario distribution induced by `sampler`.

The attribute [`NumUpperTrials`](@ref) is the number of sampled models and the attribute [`NumEvalSamples`](@ref) is the size of the evaluation models. The confidence level can be set through the [`Confidence`](@ref) attribute.

The supplied `decision` must match the defined decision variables in `stochasticmodel`. If an optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.
