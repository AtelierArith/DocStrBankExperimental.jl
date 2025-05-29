```
unfold_spectrum(spect::DataSample, n::Int) → unfolded::UnfoldedSpectrum
```

Return the unfolded spectrum of `spect` by fitting a polynomial of degree `n`  to the integrated density of states.

## Arguments

  * `n` : Degree of polynomial moddeling the smooth part of the integrated density of states.
