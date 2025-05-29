```
VARIMASettings(...)
```

Define an immutable structure to manage VARIMA specifications.

# Arguments

  * `Y_levels`: Observed measurements (`nxT`) - in levels
  * `Y`: Observed measurements (`nxT`) - differenced and demeaned
  * `μ`: Sample average (per series)
  * `n`: Number of series
  * `d`: Degree of differencing
  * `p`: Order of the autoregressive model
  * `q`: Order of the moving average model
  * `nr`: n*max(p, q+1)
  * `np`: n*p
  * `nq`: n*q
  * `nnp`: (n^2)*p
  * `nnq`: (n^2)*q
