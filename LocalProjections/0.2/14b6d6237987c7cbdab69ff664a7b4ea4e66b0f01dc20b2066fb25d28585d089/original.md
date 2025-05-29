```
irf(r::LocalProjectionResult, yname::VarName, xwname::VarName; lag::Int=0)
```

Return the [`ImpulseResponse`](@ref) of outcome variable `yname` with respect to variable `xwname` based on the estimation result `r`. If `lag` is not specified, `xwname` is assumed to be contemporaneous.
