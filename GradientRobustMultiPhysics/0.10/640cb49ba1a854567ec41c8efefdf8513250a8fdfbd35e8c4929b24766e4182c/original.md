```
function Base.div(UD::AbstractUserDataType; quadorder = UD.quadorder - 1)
```

Provides a DataFunction with the same dependencies that evaluates the divergence of the DataFunction UD. The derivatives are computed by ForwardDiff.
