```
fuv_grating1_ea(lamA[,order = -2])
```

Calculate effective area in cm^2 at a desired wavelength (Angstrom) and grating order -1 or -2.

The calculation of the effective area is based on the updated grating calibration using the procedures described in [Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract).  This function is used for flux calibration of count spectrum.

...

# Arguments

## Required

  * `lam::Number`: Wavelength in Angstrom.

## Optional

-`order::Int`: Grating order -1 or -2. ...

# Example

```jldoctest
julia> fuv_grating1_ea(1450.4,order=-2)
4.071442845470301
```
