```
function eval_curl(UD::AbstractUserDataType) -> Function
```

Provides a function that evaluates and returns the curl of the DataFunction UD in x (and t if UD depends on time). Which kind of curl is returned depends on argsizes[1]. For argsizes[1] = 1, the curl for scalar-valued functions in 2D is calculated, if argsizes[1] = 2 the curl for vector fields in 2D is calculated, and for argsies[1] = 3 the 3D curl is calculated. The derivatives are computed by ForwardDiff.
