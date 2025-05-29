```
CFIM(ρ::Matrix{T}, dρ::Vector{Matrix{T}}, M; eps=GLOBAL_EPS) where {T<:Complex}
```

Calculate the classical Fisher information matrix (CFIM). 

  * `ρ`: Density matrix.
  * `dρ`: Derivatives of the density matrix with respect to the unknown parameters to be estimated. For example, drho[1] is the derivative vector with respect to the first parameter.
  * `M`: A set of positive operator-valued measure (POVM). The default measurement is a set of rank-one symmetric informationally complete POVM (SIC-POVM).
  * `eps`: Machine epsilon.
