```
(psf::VectorPSF)(x::Real, y::Real, z::Real)
```

Compute PSF intensity at given position by summing squared field amplitudes.

# Arguments

  * `x, y`: Lateral position in microns relative to PSF center
  * `z`: Axial position in microns representing depth above the coverslip

# Returns

  * Total intensity |Ex|² + |Ey|²

# Notes

  * For single dipole: evaluates intensity from field amplitude
  * For rotating dipole: calculates incoherent sum over three orthogonal dipole orientations
