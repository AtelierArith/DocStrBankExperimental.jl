```
fit_mle(::Type{<:Weibull}, x::AbstractArray{<:Real}; 
alpha0::Real = 1, maxiter::Int = 1000, tol::Real = 1e-16)
```

Compute the maximum likelihood estimate of the [`Weibull`](@ref) distribution with Newton's method.
