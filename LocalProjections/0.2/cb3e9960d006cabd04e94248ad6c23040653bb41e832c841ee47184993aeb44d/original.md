```
vcov(r::LocalProjectionResult, horz::Int, xwname1::VarName; kwargs...)
```

Return the variance of the estimate at horizon `horz` for variable with column name `xwname1`. If `xwname2` is specified, return the covariance between `xwname1` and `xwname2`.

# Keywords

  * `yname1::VarName=r.ynames[1]`: name of the outcome variable for `xwname1`.
  * `lag1::Int=0`: lag of variable `xwname1`; being 0 means the variable is contemporaneous.
  * `xwname2::VarName=xwname1`: the second variable involved in the covariance.
  * `yname2::VarName=yname1`: name of the outcome variable for `xwname1`.
  * `lag2::Int=lag1`: lag of variable `xwname2`; being 0 means the variable is contemporaneous.
