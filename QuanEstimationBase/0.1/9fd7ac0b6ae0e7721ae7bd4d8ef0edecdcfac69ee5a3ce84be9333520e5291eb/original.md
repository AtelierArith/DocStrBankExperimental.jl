```
QFIM(ρ::Matrix{T}, dρ::Matrix{T}; LDtype=:SLD, exportLD::Bool= false, eps=GLOBAL_EPS) where {T<:Complex}
```

Calculation of the quantum Fisher information (QFI) for all types. 

  * `ρ`: Density matrix.
  * `dρ`: Derivatives of the density matrix with respect to the unknown parameters to be estimated. For example, drho[1] is the derivative vector with respect to the first parameter.
  * `LDtype`: Types of QFI (QFIM) can be set as the objective function. Options are `:SLD` (default), `:RLD` and `:LLD`.
  * `exportLD`: export logarithmic derivatives apart from F.
  * `eps`: Machine epsilon.
