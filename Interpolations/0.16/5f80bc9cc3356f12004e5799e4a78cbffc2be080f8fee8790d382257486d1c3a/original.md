```
ChainRulesCore.rrule(itp::AbstractInterpolation, x...)
```

ChainRulesCore.jl `rrule` for integration with automatic differentiation libraries. Note that it gives the gradient only with respect to the evaluation point `x`, and not the data inside `itp`.
