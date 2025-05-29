```
QFIM_Kraus(ρ0::AbstractMatrix, K::AbstractVector, dK::AbstractVector; LDtype=:SLD, exportLD::Bool=false, eps=GLOBAL_EPS)
```

Calculation of the quantum Fisher information (QFI) and quantum Fisher information matrix (QFIM) with Kraus operator(s) for all types.

  * `ρ0`: Density matrix.
  * `K`: Kraus operator(s).
  * `dK`: Derivatives of the Kraus operator(s) on the unknown parameters to be estimated. For example, dK[0] is the derivative vector on the first parameter.
  * `LDtype`: Types of QFI (QFIM) can be set as the objective function. Options are `:SLD` (default), `:RLD` and `:LLD`.
  * `exportLD`: Whether or not to export the values of logarithmic derivatives. If set True then the the values of logarithmic derivatives will be exported.
  * `eps`: Machine epsilon.
