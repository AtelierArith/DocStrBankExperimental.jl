```
TimeDerivative(p::Process [, τ])
```

Turn an existing process into a time derivative by creating `τ * Differential(t)(LHS(p)) ~ RHS(p)`.
