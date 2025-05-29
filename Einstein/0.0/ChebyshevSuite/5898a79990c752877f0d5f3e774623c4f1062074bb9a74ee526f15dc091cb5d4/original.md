```
cheb_gauss_points([TF=Float64], n::Integer) where {TF<:AbstractFloat}
cheb_gauss_points([TF=Float64], n::Integer, lower_bound::TF, upper_bound::TF) where {TF<:AbstractFloat}
```

Generate Chebyshev points of the 2nd kind.

For the standard interval [-1,1]:

$$
x_k = -\cos\left(\frac{(2k + 1)\pi}{2n}\right), \quad k = 0,1,\ldots,n-1
$$

For mapped interval [lower*bound,upper*bound]:

$$
x_{\mathrm{mapped}} = \frac{x_{\mathrm{max}} + x_{\mathrm{min}}}{2} + \frac{x_{\mathrm{min}} - x_{\mathrm{max}}}{2}x_k
$$

# Arguments

  * `TF`: Type parameter for the grid points (e.g., Float64)
  * `n`: Number of points
  * `lower_bound`: (Optional) Lower bound of the mapped interval
  * `upper_bound`: (Optional) Upper bound of the mapped interval

# References

  * [chebfun/@chebtech1/chebpts.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech1/chebpts.m)
