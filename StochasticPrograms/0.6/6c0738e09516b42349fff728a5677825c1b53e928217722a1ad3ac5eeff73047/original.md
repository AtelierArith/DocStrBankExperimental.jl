```
EWS(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

Approximately calculate the **expected wait-and-see result** (`EWS`) of the two-stage `stochasticmodel` to the current confidence level, over the scenario distribution induced by `sampler`.

The attribute [`NumEWSSamples`](@ref) is the size of the sampled models used to generate the interval and generally governs how tight it is. The confidence level can be set through the [`Confidence`](@ref) attribute.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`VRP`](@ref), [`WS`](@ref)
