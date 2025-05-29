```
load_data!(library::SpectralLibrary)
```

Load and preprocess spectral data associated with the `SpectralLibrary` object.

  * Load spectral data from a CSV-like file `library.file_name`.
  * Process wavelength ignore regions into paired sets `library.wavelength_regions_ignore`.
  * Load `library.spectra`, `library.classes`, and `library.class_valid_keys`.
  * Sort and load `library.wavelengths` as nanometers and rearrange spectral data accordingly.
  * Generate mask `library.good_bands` based on `library.wavelength_regions_ignore`.

# Returns

  * The updated `SpectralLibrary` instance with loaded and processed data.
