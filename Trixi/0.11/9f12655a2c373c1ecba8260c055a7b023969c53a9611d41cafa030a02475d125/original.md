```
SteadyStateCallback(; abstol=1.0e-8, reltol=1.0e-6)
```

Terminates the integration when the [`residual_steady_state(du, equations)`](@ref) falls below the threshold specified by `abstol, reltol`.
