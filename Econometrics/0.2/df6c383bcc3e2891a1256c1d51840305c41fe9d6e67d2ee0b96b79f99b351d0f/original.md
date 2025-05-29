```
confint(obj::EconometricModel; se::AbstractVector{<:Real} = stderror(obj), level::Real = 0.95)
```

Compute the confidence intervals for coefficients, with confidence level `level` (by default, 95%). `se` can be provided as a precomputed value.
