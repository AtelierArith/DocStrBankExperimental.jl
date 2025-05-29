```
EVPI(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

Approximately calculate the **expected value of perfect information** (`EVPI`) of the two-stage `stochasticmodel` to the current confidence level, over the scenario distribution induced by `sampler`.

In other words, calculate confidence intervals around `VRP` and `EWS`. If they do not overlap, the EVPI is statistically significant, and a confidence interval is calculated and returned.

The attribute [`NumSamples`](@ref) is the size of the sampled models used to generate the interval and generally governs how tight it is. The attribute [`NumLowerTrials`](@ref) is the number of sampled models used in the lower bound calculation and the attribute [`NumUpperTrials`](@ref) is the number of sampled models used in the upper bound calculation. The attribute [`NumEvalSamples`](@ref) is the size of the sampled models used in the upper bound calculation. The confidence level can be set through the [`Confidence`](@ref) attribute.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`VRP`](@ref), [`EWS`](@ref), [`VSS`](@ref)
