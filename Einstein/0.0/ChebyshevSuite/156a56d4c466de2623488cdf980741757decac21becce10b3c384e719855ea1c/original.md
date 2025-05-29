```
cheb_lobatto_barycentric_weights([TF=Float64], n::Integer) where {TF<:AbstractFloat}
```

Compute the barycentric weights for Chebyshev points of the 2nd kind.

# Arguments

  * `TF`: Type parameter for the weights (e.g., Float64)
  * `n`: Number of points

# References

  * [chebfun/@chebtech2/barywts.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech2/barywts.m)

See also: [`BarycentricInterpolation`](@ref)
