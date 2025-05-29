```
BQCRB(x::AbstractVector, p, dp, rho, drho; b=nothing, db=nothing, LDtype=:SLD, btype=1, eps=GLOBAL_EPS)
```

Calculation of the Bayesian quantum Cramer-Rao bound (BQCRB).

  * `x`: The regimes of the parameters for the integral.
  * `p`: The prior distribution.
  * `dp`: Derivatives of the prior distribution with respect to the unknown parameters to be estimated. For example, dp[0] is the derivative vector on the first parameter.
  * `rho`: Parameterized density matrix.
  * `drho`: Derivatives of the parameterized density matrix (rho) with respect to the unknown parameters to be estimated.
  * `b`: Vector of biases of the form $\textbf{b}=(b(x_0),b(x_1),\dots)^{\mathrm{T}}$.
  * `db`: Derivatives of b on the unknown parameters to be estimated, It should be expressed as $\textbf{b}'=(\partial_0 b(x_0),\partial_1 b(x_1),\dots)^{\mathrm{T}}$.
  * `LDtype`: Types of QFI (QFIM) can be set as the objective function. Options are "SLD" (default), "RLD" and "LLD".
  * `btype`: Types of the BCRB. Options are 1, 2 and 3.
  * `eps`: Machine epsilon.
