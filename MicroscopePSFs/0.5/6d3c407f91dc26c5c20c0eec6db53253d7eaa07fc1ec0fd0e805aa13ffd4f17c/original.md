```
save_psf(filename::String, object; metadata::Dict=Dict())
```

Save a PSF or related object (e.g., ZernikeCoefficients, PupilFunction) to an HDF5 file.

# Arguments

  * `filename`: Path where the PSF will be saved
  * `object`: Object to save (PSF, ZernikeCoefficients, PupilFunction, etc.)
  * `metadata`: Optional dictionary of additional metadata to include

# Returns

  * `filename` for chaining
