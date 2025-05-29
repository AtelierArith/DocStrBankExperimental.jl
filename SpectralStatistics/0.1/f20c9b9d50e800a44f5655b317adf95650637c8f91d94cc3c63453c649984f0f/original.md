```
unfold_spectrum(spect::DataSample, n::Int, cut_values) → unfolded::UnfoldedSpectrum
```

Return the unfolded spectrum of `spect` by piecewise fitting polynomials of degree `n`  to the integrated density of states.

## Arguments

  * `cut_values` : Relative positions of the cuts between the spectral pieces.
