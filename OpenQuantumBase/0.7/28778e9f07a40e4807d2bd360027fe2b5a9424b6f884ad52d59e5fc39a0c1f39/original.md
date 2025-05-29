```julia
mutable struct CustomBath{lambshift} <: OpenQuantumBase.AbstractBath
```

An custum bath object defined by the two-point correlation function and the corresponding spectrum.

  * `cfun`: correlation function
  * `γ`: spectrum
  * `lamb`: lambshift S function
