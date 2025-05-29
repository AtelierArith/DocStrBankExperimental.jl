```
radialpolynomial(n::Integer, m::Integer, ρ::Real) -> Real
```

Compute the unnormalized radial component R_n^m(ρ) of the Zernike polynomial.

# Arguments

  * `n`: Radial order
  * `m`: Azimuthal order (absolute value of azimuthal frequency)
  * `ρ`: Radial coordinate (0 ≤ ρ ≤ 1)

# Notes

  * Returns 0 for ρ > 1
  * No normalization applied - returns the standard mathematical form
