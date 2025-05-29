```
function H(UD::AbstractUserDataType; quadorder = UD.quadorder - 2) -> DataFunction
```

Provides a DataFunction with the same dependencies that evaluates the Hessian of the DataFunction UD. The derivatives are computed by ForwardDiff.
