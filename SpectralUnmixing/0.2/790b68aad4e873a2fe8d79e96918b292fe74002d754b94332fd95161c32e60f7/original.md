```
filter_by_class!(library::SpectralLibrary)
```

Filter spectra in the `SpectralLibrary` based on `library.class_valid_keys`.

  * Update `library.spectra` and `library.classes` to include only those matching `library.

class*valid*keys`.

# Notes

  * This function modifies the `library` in place.
  * If `library.class_valid_keys` is `nothing`, logs a message indicating that no filtering

will occur, and exits without making any changes.
