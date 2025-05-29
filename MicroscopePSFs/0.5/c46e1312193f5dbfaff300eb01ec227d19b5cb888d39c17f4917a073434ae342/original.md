```
amplitude(psf::VectorPSF, x::Real, y::Real, z::Real)
```

Compute complex vector amplitude at given position.

# Arguments

  * `psf`: Vector PSF instance
  * `x, y`: Lateral position in microns relative to PSF center
  * `z`: Axial position in microns representing depth above the coverslip

# Returns

  * Vector [Ex, Ey] of complex field amplitudes

# Notes

  * z coordinate represents the depth above the coverslip
  * z_stage in the PSF indicates the distance the stage was moved away from the nominal focal plane
  * Includes both UAF and SAF contributions automatically
  * Not meaningful for rotating dipoles (throws an error if PSF has multiple pupils)
