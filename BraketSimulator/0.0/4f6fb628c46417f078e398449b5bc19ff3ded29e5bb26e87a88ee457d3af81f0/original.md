```
DensityMatrixSimulator{T, S<:AbstractMatrix{T}} <: AbstractSimulator
```

Simulator representing evolution of a density matrix of type `S`, with element type `T`. Density matrix simulators should be used to simulate circuits with noise.
