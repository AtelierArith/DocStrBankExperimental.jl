```
cheb_lobatto_coeffs2vals_matrix([TF=Float64], n::Integer) where {TF<:AbstractFloat}
```

Construct the synthesis matrix S that transforms Chebyshev coefficients to function values at Chebyshev points of the 2nd kind.

# Arguments

  * `TF`: Element type (defaults to Float64)
  * `n`: Number of points/coefficients
