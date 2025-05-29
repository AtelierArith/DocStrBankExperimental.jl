```
evaluate_decision(stochasticmodel::StochasticModel{2}, decision::AbstractVector, sampler::AbstractSampler; kw...)
```

Return a statistical estimate of the objective of the two-stage `stochasticmodel` at `decision` in the form of a confidence interval at the current confidence level, over the scenario distribution induced by `sampler`.

In other words, evaluate `decision` on a sampled model and generate an confidence interval using the sample variance of the evaluation. The confidence level can be set through the [`Confidence`](@ref) attribute and the sample size can be set through the [`NumEvalSamples`](@ref) attribute.

The supplied `decision` must match the defined decision variables in `stochasticmodel`. If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`confidence_interval`](@ref)
