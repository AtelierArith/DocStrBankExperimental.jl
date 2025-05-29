```
cheb_gauss_barycentric_weights([TF=Float64], n::Integer) where {TF<:AbstractFloat}
```

Compute the barycentric weights for Chebyshev points of the 1st kind.

# Arguments

  * `TF`: Type parameter for the weights (defaults to Float64)
  * `n`: Number of points

# References

  * [berrut2004barycentric](@citet*)
  * [chebfun/@chebtech1/barywts.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech1/barywts.m)

See also: [`BarycentricInterpolation`](@ref)
