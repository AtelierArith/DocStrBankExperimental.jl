```
brightness_normalize!(library::SpectralLibrary)
```

Normalize `library.spectra` based on the RMS brightness of `library.good_bands`.

# Notes

  * This function modifies the `library` in place.
  * Only considers `library.good_bands` in the brightness calculation.
