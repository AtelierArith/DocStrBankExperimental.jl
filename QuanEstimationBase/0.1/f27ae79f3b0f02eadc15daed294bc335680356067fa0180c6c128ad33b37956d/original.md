```
NHB(ρ::AbstractMatrix, dρ::AbstractVector, W::AbstractMatrix)
```

Nagaoka-Hayashi bound (NHB) via the semidefinite program (SDP).

  * `ρ`: Density matrix.
  * `dρ`: Derivatives of the density matrix on the unknown parameters to be estimated. For example, drho[0] is the derivative vector on the first parameter.
  * `W`: Weight matrix.
