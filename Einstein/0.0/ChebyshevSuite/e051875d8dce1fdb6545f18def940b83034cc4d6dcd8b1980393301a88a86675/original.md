```
cheb_gauss_angles(TF, n) where {TF<:AbstractFloat}
```

Compute angles for Chebyshev points of the 1st kind:

$$
\theta_k = \frac{(2k + 1)\pi}{2n}, \quad k = n-1,\ldots,0
$$

# Arguments

  * `TF`: Type parameter for the angles (e.g., Float64)
  * `n`: Number of points
