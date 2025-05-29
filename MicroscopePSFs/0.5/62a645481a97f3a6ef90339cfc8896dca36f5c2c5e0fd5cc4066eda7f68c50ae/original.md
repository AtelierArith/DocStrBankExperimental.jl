```
load_psf(filename::String)
```

Load a PSF or related object (e.g., ZernikeCoefficients, PupilFunction) from an HDF5 file.

# Arguments

  * `filename`: Path to the HDF5 file containing a saved PSF object

# Returns

  * The loaded object with its original type (PSF, ZernikeCoefficients, PupilFunction, etc.)

# Examples

```julia
# Load a previously saved PSF
psf = load_psf("my_airy_psf.h5")

# Use the loaded PSF normally
intensity = psf(0.1, 0.2)

# Load Zernike coefficients and use them
zc = load_psf("zernike_coeffs.h5")
psf = ScalarPSF(1.4, 0.532, 1.518; zernike_coeffs=zc)
```

See also: [`save_psf`](@ref)
