```
Bayes(x, p, rho, y; M=nothing, savefile=false)
```

Bayesian estimation. The prior distribution is updated via the posterior distribution obtained by the Bayes’ rule and the estimated value of parameters obtained via the maximum a posteriori probability (MAP).

  * `x`: The regimes of the parameters for the integral.
  * `p`: The prior distribution.
  * `rho`: Parameterized density matrix.
  * `y`: The experimental results obtained in practice.
  * `M`: A set of positive operator-valued measure (POVM). The default measurement is a set of rank-one symmetric informationally complete POVM (SIC-POVM).
  * `savefile`: Whether or not to save all the posterior distributions.
