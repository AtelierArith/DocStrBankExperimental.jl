```
function eval_∇(UD::AbstractUserDataType) -> Function
```

Provides a function that evaluates and returns the Hessian of the DataFunction UD in x (and t if UD depends on time). The derivatives are computed by ForwardDiff.
