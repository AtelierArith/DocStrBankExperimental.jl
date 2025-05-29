```
purity(ρ::QuantumObject)
```

Calculate the purity of a [`QuantumObject`](@ref): $\textrm{Tr}(\rho^2)$

Note that this function only supports for [`Ket`](@ref), [`Bra`](@ref), and [`Operator`](@ref)
