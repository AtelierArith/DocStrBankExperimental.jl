```
function eval_div(UD::AbstractUserDataType) -> Function
```

Provides a function that evaluates and returns the divergence of the DataFunction UD in x (and t if UD depends on time). The derivatives are computed by ForwardDiff.
