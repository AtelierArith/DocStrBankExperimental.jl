```
remove_wavelength_region_inplace!(library::SpectralLibrary, set_as_nans::Bool=false)
```

Remove wavelength regions from `library` outside `library.good_bands` either by setting them to NaN or by filtering them out.

# Notes

  * This function modifies the `library` in place.
