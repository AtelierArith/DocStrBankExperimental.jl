```
coef(r::LocalProjectionResult, horz::Int, xwname::VarName; kwargs...)
```

Return the coefficient estimate at horizon `horz` for variable with column name `xwname`.

# Keywords

  * `yname::VarName=r.ynames[1]`: name of the outcome variable.
  * `lag::Int=0`: lag of variable `xwname`; being 0 means the variable is contemporaneous.
