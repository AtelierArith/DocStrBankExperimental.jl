```
SoftLog(x::Union{T, AbstractVector{T}}; eps::Real=1e-20) where T<:Number
```

Computes `log(x + eps)` to avoid `NaN` errors in automatic differentiation.
