```
zernikepolynomial(n::Integer, l::Integer, ρ::Real, ϕ::Real) -> Real
```

Compute the complete Zernike polynomial Z_n^l(ρ,ϕ) with Noll normalization (RMS=1).

# Arguments

  * `n`: Radial order
  * `l`: Azimuthal frequency (signed)
  * `ρ`: Radial coordinate (0 ≤ ρ ≤ 1)
  * `ϕ`: Azimuthal angle in radians

# Notes

  * Uses Noll normalization where RMS=1 over unit circle
  * Combines radial polynomial with appropriate trigonometric function
