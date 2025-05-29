```
Logistic{T<:AbstractFloat} <: Real

Logistic(t::Real)
Logistic{T}(t::Real) where {T<:AbstractFloat}
```

A type representing real numbers in $[0,1]$ (e.g. probabilities) by their  logit values.

!!! warning
    Do not use `Logistic` to convert number types! For example,  `Logistic(0.39)` equals $\operatorname{logistic}(0.39) \approx 0.60$  rather than $0.39$ in value. To convert a number to an equivalent  `Logistic` instance, use [`logisticate`](@ref) or `convert(Logistic, x)`.

