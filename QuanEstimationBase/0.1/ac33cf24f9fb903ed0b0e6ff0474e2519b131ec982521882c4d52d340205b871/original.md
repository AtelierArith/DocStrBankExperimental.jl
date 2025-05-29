```
QVTB(x::AbstractVector, p, dp, rho, drho; LDtype=:SLD, eps=GLOBAL_EPS)
```

Calculation of the Bayesian version of Cramer-Rao bound in troduced by Van Trees (VTB).

  * `x`: The regimes of the parameters for the integral.
  * `p`: The prior distribution.
  * `dp`: Derivatives of the prior distribution with respect to the unknown parameters to be estimated. For example, dp[0] is the derivative vector on the first parameter.
  * `rho`: Parameterized density matrix.
  * `drho`: Derivatives of the parameterized density matrix (rho) with respect to the unknown parameters to be estimated.
  * `LDtype`: Types of QFI (QFIM) can be set as the objective function. Options are "SLD" (default), "RLD" and "LLD".
  * `eps`: Machine epsilon.
