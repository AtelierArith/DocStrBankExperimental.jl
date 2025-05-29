```
MLE(x, rho, y; M=nothing, savefile=false)
```

Bayesian estimation. The estimated value of parameters obtained via the maximum likelihood estimation (MLE).

  * `x`: The regimes of the parameters for the integral.
  * `rho`: Parameterized density matrix.
  * `y`: The experimental results obtained in practice.
  * `M`: A set of positive operator-valued measure (POVM). The default measurement is a set of rank-one symmetric informationally complete POVM (SIC-POVM).
  * `savefile`: Whether or not to save all the posterior distributions.
