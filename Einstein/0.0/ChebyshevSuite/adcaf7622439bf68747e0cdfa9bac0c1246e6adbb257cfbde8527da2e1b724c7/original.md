```
cheb_lobatto_angles(TF, n) where {TF<:AbstractFloat}
```

Compute angles for Chebyshev points of the 2nd kind:

$$
\theta_k = \frac{k\pi}{n-1}, \quad k = n-1,\ldots,0
$$

# Arguments

  * `TF`: Type parameter for the angles (e.g., Float64)
  * `n`: Number of points
