```
TaylorModelReachSet{N, S} <: AbstractTaylorModelReachSet{N}
```

Reach-set representation consisting of a vector of taylor models in one variable (the "time" variable) whose coefficients are multivariate polynomials (the "space" variables).

### Notes

The parameters `N` and `S` refer to the numerical type of the representation (used for the Taylor model in time and Taylor series polynomials respectively). The space variables are assumed to be normalized to the interval `[-1, 1]`. It is assumed that the time domain is the same for all components.
