```
RelativePartialRandomizationAAFT(α = 0.5)
```

`RelativePartialRandomizationAAFT` surrogates are similar to [`RelativePartialRandomization`](@ref) surrogates, but add a rescaling step, so that the surrogate has the same values as the original time series (analogous to the rescaling done for [`AAFT`](@ref) surrogates).
