```
interpolate_library_to_new_wavelengths!(library::SpectralLibrary, new_wavelengths::Array
{Float64})
```

Interpolate `library` spectra to new wavelengths.

  * Perform linear interpolation, applying a flat extrapolation boundary condition.
  * Update `library.wavelengths`, `library.good_bands`, and `library.spectra` matrix to the

resampled spectra.

# Notes

  * This function modifies the `library` in place
