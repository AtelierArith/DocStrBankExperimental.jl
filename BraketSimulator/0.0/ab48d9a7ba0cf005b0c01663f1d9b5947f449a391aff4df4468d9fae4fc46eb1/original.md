```
StateVectorSimulator{T, S<:AbstractVector{T}} <: AbstractSimulator
```

Simulator representing a pure state evolution of a statevector of type `S`, with element type `T`. State vector simulators should be used to simulate circuits without noise.
