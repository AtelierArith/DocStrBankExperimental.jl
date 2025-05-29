```julia
struct MQGP{T}
```

Belief model struct and function for multiple quantities with 2D inputs.

Designed on top of a Multi-Quantity Gaussian Process, but can still be used with a single quantity.

Its interface: `X -> μ, σ` (SampleInputs -> means, standard deviations)
