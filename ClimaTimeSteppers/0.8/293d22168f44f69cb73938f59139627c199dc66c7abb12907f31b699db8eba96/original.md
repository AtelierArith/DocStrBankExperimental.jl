```
ForwardDiffJVP(; default_step = ForwardDiffStepSize3(), step_adjustment = 1)
```

Computes the Jacobian-vector product using the forward difference approximation `j(x) * Δx = (f(x + ε * Δx) - f(x)) / ε`, where `ε = step_adjustment * default_step(Δx, x)`.
