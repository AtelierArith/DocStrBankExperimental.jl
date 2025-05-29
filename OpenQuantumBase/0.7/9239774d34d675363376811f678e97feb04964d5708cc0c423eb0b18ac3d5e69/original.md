```julia
struct EnsembleFluctuator{T} <: OpenQuantumBase.StochasticBath
```

An ensemble of random telegraph noise.

  * `f`: A list of RTNs
