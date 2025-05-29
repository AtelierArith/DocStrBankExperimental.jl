```
cheb_series_integration_matrix([TR=Float64], n::Integer) where {TR<:AbstractFloat}
cheb_series_integration_matrix([TR=Float64], n::Integer, lower_bound::TR, upper_bound::TR) where {TR<:AbstractFloat}
```

Generate the Chebyshev coefficient integration matrix that maps Chebyshev coefficients to the coefficients of the integral of the interpolating polynomial.

# Arguments

  * `TR`: Type parameter for the matrix elements (e.g., Float64)
  * `n`: Size of the matrix (n×n)
  * `lower_bound`: (Optional) Lower bound of the integration interval
  * `upper_bound`: (Optional) Upper bound of the integration interval

# References

  * [chebfun/@chebcolloc1/chebcolloc1.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc1/chebcolloc1.m)
  * [chebfun/@chebcolloc2/chebcolloc2.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebcolloc2/chebcolloc2.m)
