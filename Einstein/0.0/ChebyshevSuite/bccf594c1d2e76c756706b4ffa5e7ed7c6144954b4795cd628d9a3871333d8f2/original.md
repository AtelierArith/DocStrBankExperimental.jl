```
cheb_lobatto_differentiation_matrix([TR=Float64], n::Integer, k::Integer=1) where {TR<:AbstractFloat}
```

Construct a Chebyshev differentiation that maps function values at `n` Chebyshev points of the 2nd kind  to values of the `k`-th derivative of the interpolating polynomial at those points.

# Arguments

  * `TR`: Element type (defaults to Float64)
  * `n::Integer`: Number of Chebyshev points
  * `k::Integer=1`: Order of the derivative (default: 1)

# References

  * [chebfun/@chebcolloc2/chebcolloc2.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc2/chebcolloc2.m)
