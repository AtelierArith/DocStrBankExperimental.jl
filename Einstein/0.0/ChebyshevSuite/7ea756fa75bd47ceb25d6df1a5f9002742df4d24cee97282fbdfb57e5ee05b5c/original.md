```
cheb_series_derivative!(coeffs::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
cheb_series_derivative!(coeffs_der::AbstractVector{TFC}, coeffs::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
cheb_series_derivative(coeffs::AbstractVector{TFC}) where {TFC<:Union{AbstractFloat,Complex{<:AbstractFloat}}}
```

Compute derivatives of coefficients of Chebyshev series.

# Arguments

  * `coeffs`: Input vector of Chebyshev coefficients with length n

# References

  * [chebfun/@chebtech/diff.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/diff.m)
