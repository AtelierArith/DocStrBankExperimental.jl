```
evaluate(x, δt)
```

Evaluates each element of `x::AbstractArray{Taylor1{T}}`, representing the dependent variables of an ODE, at *time* δt. Note that the syntax `x(δt)` is equivalent to `evaluate(x, δt)`, and `x()` is equivalent to `evaluate(x)`.
