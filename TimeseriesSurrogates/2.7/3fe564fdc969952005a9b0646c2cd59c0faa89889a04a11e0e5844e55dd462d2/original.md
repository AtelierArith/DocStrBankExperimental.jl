```
SpectralPartialRandomizationAAFT(α = 0.5)
```

`SpectralPartialRandomizationAAFT` surrogates are similar to [`PartialRandomization`](@ref) surrogates, but add a rescaling step, so that the surrogate has the same values as the original time series (analogous to the rescaling done for [`AAFT`](@ref) surrogates).
