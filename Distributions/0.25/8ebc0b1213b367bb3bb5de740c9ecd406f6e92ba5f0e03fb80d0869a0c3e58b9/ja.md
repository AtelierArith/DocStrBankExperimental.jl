```
fit_mle(::Type{<:Weibull}, x::AbstractArray{<:Real}; 
alpha0::Real = 1, maxiter::Int = 1000, tol::Real = 1e-16)
```

ニュートン法を用いて[`Weibull`](@ref)分布の最尤推定値を計算します。
