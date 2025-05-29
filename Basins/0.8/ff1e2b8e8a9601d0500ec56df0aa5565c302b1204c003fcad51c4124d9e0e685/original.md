```
uncertainty_exponent(bsn::BasinInfo, integ; precision=1e-3) -> α,e,ε,f_ε
```

This function estimates the uncertainty exponent of the boundary. It is related to the uncertainty dimension.

[C. Grebogi, S. W. McDonald, E. Ott, J. A. Yorke, Final state sensitivity: An obstruction to predictability, Physics Letters A, 99, 9, 1983]

## Arguments

  * `bsn` : structure that holds the information of the basin.
  * `integ` : handle to the iterator of the dynamical system.

## Keyword arguments

  * `precision` variance of the estimator of the uncertainty function.
