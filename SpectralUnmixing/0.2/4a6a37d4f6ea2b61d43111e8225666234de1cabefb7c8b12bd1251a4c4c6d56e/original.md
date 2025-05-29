```
split_library(library::SpectralLibrary, split_fraction::Float64)
```

Split a `SpectralLibrary` into two new libraries based on a specified fraction of the total spectra.

# Returns

  * `Tuple{SpectralLibrary, SpectralLibrary}` with each output library a random,

mutually exclusive subset of the original library containing `split_fraction` and `1 - split_fraction` of the spectra, respectively.

# Notes

  * The split is random; consecutive calls with the same `library` may yield different

results.
