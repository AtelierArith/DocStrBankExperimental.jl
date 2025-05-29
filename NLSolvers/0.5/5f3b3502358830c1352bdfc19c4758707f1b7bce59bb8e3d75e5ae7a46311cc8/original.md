```
DFSANE(memory[ = 4], sigma_limits[ = (1e-5, 1e5)])
```

Construct a method instance of the DFSANE algorithm for solving systems of non-linear equations. The memory keyword is used to control how many residual norm values to store for the non-monotoneous line search (`M` in the paper). The `sigma_limit` keyword is used to provide a tuple of values used to bound the spectral coefficient (`σ_min` and `σ_max` in the paper).

```
- decrease (γ in the paper) is used to control what amount of decrease in function value is sufficient. Must be chosen such that 0 < decrease < 1.
```

# Notes

To re-implement the setup in the numerical section of [PAPER] use

DFSANE(nexp=2,memory=10, sigma*limit=(1e-10, 1e10), decrease=1e-4, sigma*0=1.0))
