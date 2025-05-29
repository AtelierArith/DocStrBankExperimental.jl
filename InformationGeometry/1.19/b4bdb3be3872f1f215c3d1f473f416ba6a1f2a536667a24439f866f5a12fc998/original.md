```
SoftAbs(x::Union{T, AbstractVector{T}}; eps::Real=1e-100) where T<:Number
```

Computes differentiable approximation of absolute value function `abs` as `sqrt(abs2(x) + eps)`.
