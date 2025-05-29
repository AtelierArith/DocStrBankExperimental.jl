```
plot_endmembers_individually(endmember_library::SpectralLibrary;
output_name::String="", legend_on::Bool=false)
```

Plot all endmember spectra individually from a spectral library, grouped by class.

  * Create seperate plots for each class, legends are disabled by default.
  * Saves file to `output_name` if provided, otherwise defaults to no saving.
