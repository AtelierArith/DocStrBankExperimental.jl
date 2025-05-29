```
reduce_endmembers_nmf!(library::SpectralLibrary, max_endmembers_per_class::Int64)
```

Reduce the number of endmembers in the spectral library using Non-negative Matrix Factorization (NMF).

  * For each class in `library.class_valid_keys`, apply NMF to the spectra subset to identify

the specified maximum number of endmembers.

  * Update `library.classes` and `library.spectra` to contain the reduced set of endmembers.

# Notes

  * This function modifies the `library` in place.
  * Only `library.good_bands` will be considered in the NMF computation.
  * The NMF uses a maximum of 500 iterations with a tolerance of 1.0e-2 for convergence.
