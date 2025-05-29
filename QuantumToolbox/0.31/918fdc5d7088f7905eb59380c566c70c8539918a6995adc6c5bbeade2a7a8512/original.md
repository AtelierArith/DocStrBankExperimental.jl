```
fidelity(ρ::QuantumObject, σ::QuantumObject)
```

Calculate the fidelity of two [`QuantumObject`](@ref): $F(\hat{\rho}, \hat{\sigma}) = \textrm{Tr} \sqrt{\sqrt{\hat{\rho}} \hat{\sigma} \sqrt{\hat{\rho}}}$

Here, the definition is from [Nielsen-Chuang2011](@citet). It is the square root of the fidelity defined in [Jozsa1994](@citet).

Note that `ρ` and `σ` must be either [`Ket`](@ref) or [`Operator`](@ref).
