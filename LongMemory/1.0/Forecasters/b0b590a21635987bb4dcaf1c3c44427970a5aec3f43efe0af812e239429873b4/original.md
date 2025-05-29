```
gregory_coeffs(N::Int)
```

Computes the Gregory coefficients for the harmonic inverse transformation.

# Arguments

  * `N::Int`: The number of coefficients to compute.

# Output

  * `coefs::Array`: The Gregory coefficients.

# Notes

The first coefficient is 1/2 and the rest are computed using the recursive formula. The zero lag coefficient is not computed, it is theoretically 1.

# Examples

```julia
julia> gregory_coeffs(5)
```
