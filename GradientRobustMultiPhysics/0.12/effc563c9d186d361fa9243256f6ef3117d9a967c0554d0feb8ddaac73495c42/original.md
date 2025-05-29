```
function dt(UD::AbstractUserDataType; quadorder = UD.quadorder - 1) -> DataFunction
```

Provides a DataFunction with the same dependencies that evaluates the gradient of the DataFunction UD. The derivatives are computed by ForwardDiff.
