```
tearing(sys; simplify=false)
```

Tear the nonlinear equations in system. When `simplify=true`, we simplify the new residual equations after tearing. End users are encouraged to call [`structural_simplify`](@ref) instead, which calls this function internally.
