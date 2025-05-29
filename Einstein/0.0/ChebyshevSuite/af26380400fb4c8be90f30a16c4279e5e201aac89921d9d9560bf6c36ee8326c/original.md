```
cheb_lobatto_integration_matrix([TF=Float64], n::Integer) where {TF<:AbstractFloat}
cheb_lobatto_integration_matrix([TF=Float64], n::Integer, lower_bound::TF, upper_bound::TF) where {TF<:AbstractFloat}
```

Compute Chebyshev integration matrix that maps function values at `n` Chebyshev points of the 2st kind to values of the integral of the interpolating polynomial at those points, with the convention that the first value is zero.

# References

  * [chebfun/@chebcolloc2/chebcolloc2.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc2/chebcolloc2.m)
