```
ZernikeCoefficients{T<:Real}
```

Mutable structure to hold Zernike coefficients for both magnitude and phase of a pupil function. Uses Noll indexing convention starting at index 1.

# Fields

  * `mag::Vector{T}`: Coefficients for magnitude (1-indexed per Noll convention)
  * `phase::Vector{T}`: Coefficients for phase (1-indexed per Noll convention)

# Notes

  * First coefficient (index 1) typically represents piston
  * Magnitude coefficients are typically normalized with mag[1] = 1
  * Phase coefficients represent phase in radians
  * RMS normalization (Noll convention) is used so coefficients directly represent RMS wavefront error
