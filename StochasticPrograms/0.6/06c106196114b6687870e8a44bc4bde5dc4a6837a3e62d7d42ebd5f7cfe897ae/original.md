```
EEV(stochasticmodel::StochasticModel{2}, sampler::AbstractSampler)
```

Approximately calculate the **expected value of the expected value decision** (`EEV`) of the two-stage `stochasticmodel` to the current confidence level, over the scenario distribution induced by `sampler`.

The attribute [`NumEEVSamples`](@ref) is the size of the sampled models used in the eev calculation. The confidence level can be set through the [`Confidence`](@ref) attribute.

If a sample-based optimizer has not been set yet (see [`set_optimizer`](@ref)), a `NoOptimizer` error is thrown.

See also: [`EVP`](@ref), [`EV`](@ref)
