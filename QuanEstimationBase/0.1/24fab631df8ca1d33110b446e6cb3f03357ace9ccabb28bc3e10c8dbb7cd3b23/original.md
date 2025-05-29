```
VTB(x::AbstractVector, p, dp, rho, drho; M=nothing, eps=GLOBAL_EPS)
```

Calculation of the Bayesian version of Cramer-Rao bound introduced by Van Trees (VTB).

  * `x`: The regimes of the parameters for the integral.
  * `p`: The prior distribution.
  * `dp`: Derivatives of the prior distribution with respect to the unknown parameters to be estimated. For example, dp[0] is the derivative vector on the first parameter.
  * `rho`: Parameterized density matrix.
  * `drho`: Derivatives of the parameterized density matrix (rho) with respect to the unknown parameters to be estimated.
  * `M`: A set of positive operator-valued measure (POVM). The default measurement is a set of rank-one symmetric informationally complete POVM (SIC-POVM).
  * `eps`: Machine epsilon.
