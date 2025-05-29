```
BCRB(x::AbstractVector, p, dp, rho, drho; M=nothing, b=nothing, db=nothing, btype=1, eps=GLOBAL_EPS)
```

Calculation of the Bayesian Cramer-Rao bound (BCRB).

  * `x`: The regimes of the parameters for the integral.
  * `p`: The prior distribution.
  * `dp`: Derivatives of the prior distribution with respect to the unknown parameters to be estimated. For example, dp[0] is the derivative vector on the first parameter.
  * `rho`: Parameterized density matrix.
  * `drho`: Derivatives of the parameterized density matrix (rho) with respect to the unknown parameters to be estimated.
  * `M`: A set of positive operator-valued measure (POVM). The default measurement is a set of rank-one symmetric informationally complete POVM (SIC-POVM).
  * `b`: Vector of biases of the form $\textbf{b}=(b(x_0),b(x_1),\dots)^{\mathrm{T}}$.
  * `db`: Derivatives of b on the unknown parameters to be estimated, It should be expressed as $\textbf{b}'=(\partial_0 b(x_0),\partial_1 b(x_1),\dots)^{\mathrm{T}}$.
  * `btype`: Types of the BCRB. Options are 1, 2 and 3.
  * `eps`: Machine epsilon.
