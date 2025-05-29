```
(psf::AbstractPSF)(x, y)
```

Evaluate normalized PSF intensity at position (x,y) relative to PSF center.

# Arguments

  * `x, y`: Position in microns relative to PSF center

# Returns

  * Intensity normalized to integrate to 1

# Coordinates

Input coordinates (x,y) are in physical units (microns) relative to PSF center.

# Examples

```julia
psf = AiryPSF(1.4, 0.532)  # NA=1.4, λ=532nm
intensity = psf(0.1, 0.2)  # Evaluate at (0.1μm, 0.2μm)
```
