```
reduce_endmembers_kmeans!(library::SpectralLibrary, max_endmembers_per_class::Int64)
```

Reduce the number of endmembers in the spectral library using K-means clustering.

  * For each class in `library.class_valid_keys`, apply K-means clustering to the spectra

subset to identify the specified maximum number of endmembers from cluster centers.

  * Update `library.classes` and `library.spectra` to contain the reduced set of endmembers.

# Notes

  * This function modifies the `library` in place.
  * Only `library.good_bands` will be considered in the K-means computation.
  * The K-means algorithm is run with a maximum of 1000 iterations.
