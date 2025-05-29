```
bures_angle(ρ::QuantumObject, σ::QuantumObject)
```

Calculate the [Bures angle](https://en.wikipedia.org/wiki/Bures_metric) between two [`QuantumObject`](@ref): $D_A(\hat{\rho}, \hat{\sigma}) = \arccos\left(F(\hat{\rho}, \hat{\sigma})\right)$

Here, the definition of [`fidelity`](@ref) $F$ is from [Nielsen-Chuang2011](@citet). It is the square root of the fidelity defined in [Jozsa1994](@citet).

Note that `ρ` and `σ` must be either [`Ket`](@ref) or [`Operator`](@ref).
