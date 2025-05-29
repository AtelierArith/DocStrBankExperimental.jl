```
cheb_series_evaluate(coeffs::AbstractVector{TFC}, x::TF) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}
cheb_series_evaluate(coeffs::AbstractVector{TFC}, x::AbstractVector{TF}) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}
```

Evaluate Chebyshev coefficients at point(s) using Clenshaw's algorithm.

# Performance Notes

  * Clenshaw's algorithm: O(n) operations per point
  * [TODO] NDCT: O(n log n) operations for many points simultaneously

# References

  * [chebfun/@chebtech/clenshaw.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/clenshaw.m)
  * [chebfun/@chebtech/feval.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech/feval.m)
