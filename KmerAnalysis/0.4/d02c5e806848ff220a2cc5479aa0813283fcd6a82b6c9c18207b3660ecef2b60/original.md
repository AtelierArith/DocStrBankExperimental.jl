```
find_spectra_peaks(s::KmerFrequencySpectra{1})
```

Automatically detect all the peaks present in the signal of a 1D k-mer frequency spectra, using a persistent homology method.

Returns a vector of [`SpectraPeak`](@ref).
