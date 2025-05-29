```
amplitude(psf::AbstractPSF, x::Real, y::Real)
```

Evaluate complex field amplitude at position (x,y) relative to PSF center.

# Arguments

  * `x, y`: Position in microns relative to PSF center

# Returns

  * Complex amplitude normalized such that |amplitude|² gives normalized intensity

# Coordinates

Input coordinates (x,y) are in physical units (microns) relative to PSF center.

# Examples

```julia
psf = AiryPSF(1.4, 0.532)
amp = amplitude(psf, 0.1, 0.2)
intensity = abs2(amp)  # Convert to intensity
```
