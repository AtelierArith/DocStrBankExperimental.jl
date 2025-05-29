```
HCRB(ρ::AbstractMatrix, dρ::AbstractVector, W::AbstractMatrix; eps=GLOBAL_EPS)
```

Caltulate the Holevo Cramer-Rao bound (HCRB) via the semidefinite program (SDP).

  * `ρ`: Density matrix.
  * `dρ`: Derivatives of the density matrix on the unknown parameters to be estimated. For example, drho[0] is the derivative vector on the first parameter.
  * `W`: Weight matrix.
  * `eps`: Machine epsilon.
