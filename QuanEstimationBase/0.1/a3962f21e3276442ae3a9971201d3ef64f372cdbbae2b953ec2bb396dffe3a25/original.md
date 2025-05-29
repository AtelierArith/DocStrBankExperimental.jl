```
QFIM_Gauss(R̄::V, dR̄::VV, D::M, dD::VM) where {V,VV,M,VM<:AbstractVecOrMat}
```

Calculate the SLD based quantum Fisher information matrix (QFIM) with gaussian states.  

  * `R̄` : First-order moment.
  * `dR̄`: Derivatives of the first-order moment with respect to the unknown parameters to be estimated. For example, dR[1] is the derivative vector on the first parameter.
  * `D`: Second-order moment.
  * `dD`: Derivatives of the second-order moment with respect to the unknown parameters to be estimated.
  * `eps`: Machine epsilon.
