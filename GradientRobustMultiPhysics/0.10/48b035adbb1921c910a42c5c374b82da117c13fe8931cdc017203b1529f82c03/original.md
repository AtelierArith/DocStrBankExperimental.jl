```
function curl(UD::AbstractUserDataType; quadorder = UD.quadorder - 1)
```

Provides a DataFunction with the same dependencies that evaluates the curl of the DataFunction UD. The derivatives are computed by ForwardDiff.
