```julia
mutable struct CorrelatedBath <: OpenQuantumBase.AbstractBath
```

`CorrelatedBath` defines a correlated bath type by the matrices of its two-point correlation functions and corresponding spectrums.

  * `cfun`: correlation function
  * `γ`: spectrum
  * `inds`: bath correlator idx
