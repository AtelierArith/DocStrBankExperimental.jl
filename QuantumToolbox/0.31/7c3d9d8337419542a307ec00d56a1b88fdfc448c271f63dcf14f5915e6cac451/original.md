```
hilbert_dist(ρ::QuantumObject, σ::QuantumObject)
```

Calculates the Hilbert-Schmidt distance between two [`QuantumObject`](@ref): $D_{HS}(\hat{\rho}, \hat{\sigma}) = \textrm{Tr}\left[\hat{A}^\dagger \hat{A}\right]$, where $\hat{A} = \hat{\rho} - \hat{\sigma}$.

Note that `ρ` and `σ` must be either [`Ket`](@ref) or [`Operator`](@ref).

# References

  * [Vedral-Plenio1998](@citet)
