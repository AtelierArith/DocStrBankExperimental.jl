```
reduce_endmembers_pca!(library::SpectralLibrary, max_endmembers_per_class::Int64)
```

Reduce the number of endmembers in the spectral library using Principal Component Analysis (PCA).

  * For each class in `library.class_valid_keys`, apply PCA to the spectra subset to identify

the specified maximum number of endmembers.

  * Update `library.classes` and `library.spectra` to contain the reduced set of endmembers.

# Notes

  * This function modifies the `library` in place.
  * Only `library.good_bands` will be considered in the PCA computation.
  * The PCA is truncated to `max_endmembers_per_class` PCs per endmember class.
