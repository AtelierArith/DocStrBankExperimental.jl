```
function Δ(UD::AbstractUserDataType; quadorder = UD.quadorder - 2)
```

Provides a DataFunction with the same dependencies that evaluates the Laplacian of the DataFunction UD. The derivatives are computed by ForwardDiff.
